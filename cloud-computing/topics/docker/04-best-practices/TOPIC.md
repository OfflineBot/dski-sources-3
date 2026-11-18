# 3. Best Practices

Wichtige Konventionen zur Konfiguration von Docker Containern und Images

## Baseimage

- Das Baseimage sollte so ausgewählt werden, dass es nur die wirklich benötigte Funktionalität besitzt. Ein geringerer Funktionsumfang, reduziert die Downloaddauer, den Speicherbedarf und die Angriffsfläche:
  - ubuntu ~ 188 MB,
  - opensuse:latest ~ 82 MB
  - alpine ~ 5MB
- Es sollten offizielle Images für Baseimages bevorzugt werden, da bei diesen die Aktualisierungen und die Authentizität von Docker sichergestellt wird.
- Das Baseimage sollte mit einem Tag referenziert werden, niemals mit ‚latest‘.
- Images sollten stets bei Aktualisierungen des Baseimage neu gebaut werden. Nur so kann sichergestellt werden, dass die Container dauerhaft gepatcht sind.

### Notizen

- Wie groß der Funktionsumfang der Linux Distributionen variieren kann, lässt sich an der Speichergröße sehen: opensuse benötigt weniger als die Hälfte des Speichers von ubuntu, für die Linux Distribution ‚alpine‘ entfällt rund 35-mal weniger als für ubuntu.
- Offizielle Images: Docker unterhält für deren Aktualisierung ein eigenes Team.
- Das Baseimage wird mit einem passenden Tag referenziert. Dadurch ist es möglich, dass das Baseimage Aktualisierungen empfangen kann.
- Abgeleitete Images neu bauen: Alle Aktualisierungen und Patches der Container zur Laufzeit werden nichtig, sobald diese neu gestartet werden. Somit können dauerhafte Veränderungen der Container nur über Anpassungen der Docker Images erreicht werden.

## Tagging

- Das Weglassen einer expliziten Version, sodass ‚latest‘ gesetzt wird, ist strikt zu vermeiden da damit:
  - verschiedene Versionen in der Registry und auf dem Client referenziert werden.
  - nicht die ‚aktuelle‘, sondern die ‚unbekannte‘ Version gemeint ist.
  - keine Charakterisierung des Images erfolgt.
  - kein Rücksprung auf vorherige Versionen möglich ist.
- Für Abhängigkeiten sollten stable Tags (bspw. ‚1‘, ‚1.2‘, ‚1.2.1‘) eingesetzt werden um die neusten Änderungen zu bekommen.
- Nutzung von unique Tags für eigen erstellte Docker Images, um ungewolltes Caching zu vermeiden und Updatebedarf anzumelden
- Integration der BuildId oder Datum in unique Tags ist sinnvoll. Vorsicht bei GitTags, da sie keine Aktualisierungen der Baseimages abbilden.

![Best Practices — Tagging](images/duplicate-tags.png)

### Notizen

- Mit ‚latest‘ erfolgt keine Charakterisierung der vorgenommenen Änderungen.
- ‚stable Tags‘ sollten stets für die Nutzung in Baseimages zum Einsatz kommen, da hier über das verwendete Schema eingestellt werden kann ob nur Sicherheitsaktualisierungen oder auch Featureupdates berücksichtigt werden sollen.
- Einzigartige Tags (unique Tags) bei den erstellten Docker Images vermeiden, dass durch Caching veraltete Versionsstände ausgeliefert werden.
- BuildId: die Id des Bauvorgangs; Datum: das aktuelle Datum.
- Es sollte vermieden werden Git-Tags in die Tags einzuarbeiten.

## Umgebungsvariablen

- Umgebungsvariablen dürfen im Dockerfile nicht für sensible Daten wie Passwörter verwendet werden, da diese durch den ‘docker image history’ Befehl ausgelesen werden können.
- Stattdessen sollten sensible Daten zur Laufzeit via ‘--env’ Option eingebunden werden (vgl. MySQL image). Besser verschlüsselte Varianten nutzen.
- Bei vielen Umgebungsvariablen, die zur Laufzeit gesetzt werden, empfiehlt sich die Auslagerung in eine separate Datei, die zur Laufzeit via “--env-file” eingebunden wird.
- Lesereihenfolge: Dockerfile -> env-file -> Laufzeitargument
- Bei Umgebungsvariablen die nur zum Bau des Images verwendet werden, sollte ARG statt ENV verwendet werden.

### Notizen

- Umgebungsvariablen bieten einen universellen Mechanismus um das Verhalten einer Anwendung zur Laufzeit anzupassen.
- Lässt es sich nicht vermeiden, dass sensible Daten als Umgebungsvariable in die Anwendung integriert werden, sollten diese unbedingt erst zur Laufzeit gesetzt werden. Generell ist es empfehlenswert statt Umgebungsvariablen, verschlüsselte Mechanismen zum Transport von sensiblen Daten zu wählen.
- Sollten viele Umgebungsvariablen erst zur Laufzeit gesetzt werden kann der Docker-Befehl in der Eingabeaufforderung schnell übersichtlich werden. Um dies zu vermeiden, werden die konkreten Werte in die separate Datei ausgelagert.
- Die Werte der Umgebungsvariablen können gemäß der Lesereihenfolge überschrieben werden.
- ARG statt ENV im Dockerfile: wenn Umgebungsvariablen nur zur Erstellung der Anwendung benötigt werden und keinen Einfluss auf das Laufzeitverhalten der Anwendung ausüben.

## Schichtenarchitektur

| Änderungsfrequenz |  |
| --- | --- |
| gering | `FROM openjdk:8-jdk-alpine` |
|  | `COPY *.jar app/app.jar` |
|  | `ENV stage=prod` |
|  | `RUN mkdir app` |
|  | `WORKDIR target/` |
| hoch | `CMD ["java","-jar","/app.jar"]` |

- Die Schichtenarchitektur von Docker impliziert, dass je weiter oben ein Befehl steht, desto seltener sich dieser ändert.
  - Bei Abweichungen der Prüfsummen, wird die entsprechende Schicht und alle darunter liegenden neu gebaut
  - Schichten können nur dann wiederverwendet werden, wenn sie die gleiche Prüfsumme aufweisen
- Um unnötige Schichten zu vermeiden, empfiehlt es sich zusammengehörige RUN Befehle mit ‚&&‘ zu kombinieren.
- Die Befehle sollten stets so präzise wie möglich sein, ansonsten werden Schichten auch bei nicht relevanten Änderungen neu gebaut (insb. bei Wildcards).

### Notizen

- Damit die Vorteile der Schichtenarchitektur realisiert werden können, werden die Befehle im Dockerfile gemäß ihrer Änderungsfrequenz angeordnet: Je seltener sich ein Befehl oder dessen referenzierten Dateien ändern, desto höher im Dockerfile; je häufiger er sich ändert, desto weiter unten.
- Das Schaubild zeigt ein fehlerhaft angeordneten COPY Befehl, der die gesamten Vorteile der Schichtenbildung zunichtemacht: Das jar, das sich im Rahmen jedes Compiliervorgangs ändert, wird bereits in der zweiten Zeile in das Dockerfile kopiert. Infolgedessen werden im Rahmen jedes Compiliervorgangs Änderungen in dieser Schicht erkannt und es müssen diese, sowie alle darunter liegenden Schichten neu gebaut werden. Eine Wiederverwendung der anderen Schichten kann somit nicht umgesetzt werden.
- RUN Befehle via ‚&&‘ kombinieren: Es werden weniger Schichten benötigt und die Bauzeit eines Images wird verkürzt.
- Präzise Befehle: Es sollen wirklich nur die notwendigen Dateien in das Docker Image kopiert werden. Bei der Verwendung von Wildcards ist genaustens zu überprüfen ob wirklich nur die notwendigsten Dateien kopiert werden. Grund: Änderungen an unnötigen Dateien, die dennoch kopiert werden, stoßen ein Neubau der entsprechenden Schicht und aller darunterliegenden an.

## Non-Root Ausführung

```dockerfile
FROM openjdk:8-jdk-alpine
ENV stage=prod
RUN addgroup -S spring && adduser -S springuser -G spring
USER springuser
RUN mkdir app
WORKDIR target/
COPY *.jar app/app.jar
EXPOSE 8080
CMD ["java","-jar","/app.jar"]
```

- In der Standardkonfiguration werden alle Prozesse im Container unter dem root (Admin) Account ausgeführt.
- Ein Ausbruch aus einem Containerprozess der mit root Rechten ausgeführt wird kann kritische Auswirkungen haben. Da ein Containerprozess gleichberechtigt zu einem nativen Prozess ist.
- Mit dem Kommando ‚USER‘ können Befehle des Dockerfile unter einem unprivilegierten User ausgeführt werden.
- In der Standardkonfiguration gehören neue Benutzer der Gruppe root (Admin) an, sodass manuell eine andere Gruppe angelegt werden muss.

### Notizen

- Standardmäßig werden alle Befehle im Dockerfile unter dem Administratoraccout ‚root‘ ausgeführt.
- Das Kommando USER gibt es zur Vermeidung dieser Sicherheitsrisiken und um die Nutzung von nicht-root Benutzern zu vereinfachen. Es wird gefolgt von der konkreten UserId angegeben; alle folgenden Befehle werden mit dem spezifizierten Useraccount durchgeführt.
- Zu beachten: Erst muss der User erstellt und dann einer neuen Benutzergruppe zugewiesen werden, da neu angelegte Benutzer standardmäßig der Administratoren Gruppe zugeordnet werden.

## Hands-On

```dockerfile
FROM ubuntu
RUN apt-get update
RUN apt-get install openjdk-8-jdk -y
RUN apt-get install curl -y
RUN mkdir app
COPY target/* app/
CMD java -jar app.jar
```

- Nutzung eines kleineren Images samt präzisem Tag
- Bündelung der Anweisungen um Layer zu sparen
- Ausführung als non-root
- Explizites Copy-Statement
- Exec Notation für Sicherheit

```dockerfile
FROM openjdk:8-jre-alpine3.9
RUN apk update && apk add curl
RUN mkdir app
RUN addgroup -S spring && adduser -S springuser -G spring
USER springuser
WORKDIR app
COPY target/app.jar .
CMD ["java","-jar","app.jar"]
```

### Notizen

- Ausgangspunkt ist ein Dockerfile, das die neuste Version des Ubuntu Betriebssystem als Baseimage hat, darauf aufbauend die Java Laufzeitumgebung und Curl installiert, das Verzeichnis app erzeugt, den Inhalt des Host-Verzeichnisses „target“ hineinkopiert und die sich darin befindende Jar Datei ausführt.
- Erste Verbesserung: Austausch eines umfassenden und nicht versionierten Basisimage in ein zweckdienliches und versioniertes Basisimage.
- Die Befehle zur Installation von curl werden zusammengefasst um unnötige Schichten einzusparen. Java ist durch das Baseimage bereits installiert.
- Die weitere Ausführung sollte unter einem non-root Account stattfinden, für den der Account samt Gruppe angelegt wird.
- Der Copy Befehl kopiert nur noch die Jar Datei und nicht mehr das gesamte Verzeichnis.
- Die gewählte Shell-Notation für den Laufzeitbefehl wird in die Exec-Notation überführt um die Sicherheit weiter zu härten.

Quelle: cloud-computing/origin/WDS125 - Cloud Computing (SCA)/05 Docker/3-Docker/3-Docker.pdf, Seiten 35–40

# 2. Docker Image

Docker Image beziehen und selbst bauen

## Status Quo (Seite 18)

Welche Fehlerursachen beim Livegang einer Anwendung in der produktiven Umgebung haben Sie erlebt?

- Unterschiede in Applikationsversionen (OS, DB, Laufzeit, Webserver, etc.).
- Unterschiede in der Konfiguration (Umgebungsvariablen, Skripte, Dateien, Rechte, Zertifikate, etc.).
- Unterschiede in der Herangehensweise zur Einspielung des Updates.
- Vage Dokumentation zum Vorgehen oder kein Vorwissen zu wichtigen Konventionen.
- Fehlerhafte Übertragung der Dateien und Konfigurationen auf die Prod-Umgebung.

### Notizen

Bevor wir uns näher mit Docker Images beschäftigen, blicken wir auf häufige Ursachen
für ein fehlerhaftes Deployment. So scheitern Deployments oft, wenn unterschiedliche
Versionen von Applikationen eingesetzt werden. Ein weiterer Grund für fehlerhafte
Deployments sind unterschiedliche Konfigurationen zwischen den Maschinen, die für
den Test und den produktiven Einsatz verwendet werden. Weitere Fehlerursachen für
fehlgeschlagene Deployments sind ein unterschiedliches Vorgehen beim
Deploymentvorgang und die fehlerhafte Übertragung von Daten auf die produktive
Maschine.

## Überblick (Seite 19)

- Ein Docker Image hat einen Namen (Tag) und besteht aus den notwendigen Abhängigkeiten und Konfigurationen zur Ausführung einer Anwendung.
- Das Docker Image hat einen strukturierten Aufbau wobei jede Änderung und Konfiguration in einer eigenen Schicht samt Prüfsumme erfasst wird.
- Gemäß dem Prinzip der immutable infrastructure ist jede Schicht unveränderbar, d.h. sie wird nicht verändert sondern stets neu gebaut.
- Die Schichten eines Images lassen sich via docker image history anzeigen.

| Tag | `cloud-comp:1.1` |
| --- | --- |
| Schichten | `ENV stage prod` |
|  | `RUN apt-get install vi` |
|  | `FROM Ubuntu` |

### Notizen

Ein Docker Image trägt einen Tag (was dem Namen entspricht) und besteht aus den
Abhängigkeiten und Konfigurationen, die zur Ausführung einer Anwendung erforderlich
sind. Im Gegensatz zu dem Image einer virtuellen Maschine das als eine große Binärdatei
gespeichert wird, besitzt ein Docker Image einen strukturierten Aufbau in Schichten.
Jede Änderung am Docker Image wird in einer eigenen Schicht samt eigener Checksum
abgebildet. Durch dieses Prinzip wird gemäß dem Grundsatz von ‚immutable
infrastructure‘ sichergestellt, dass Änderungen an einer Schicht zur Folge haben, dass die
alte Schicht verworfen wird und eine neue Schicht erstellt wird. Die einzelnen Schichten
eines Docker Images lassen sich mit dem Befehl ‚docker image history‘ gefolgt vom
konkreten Imagenamen anzeigen.

## Überblick (Seite 20)

- Jede Schicht wird nur einmal gespeichert. Dadurch wird keine Änderung an einem Docker Image redundant gespeichert.
- Wenn ein Docker Image gebaut wird, werden die Prüfsummen jeder Schicht in aufsteigender Weise auf Änderungen überprüft.
- Docker Images die sich bis auf eine Änderung am Ende der Konfiguration gleichen belegen dadurch nur einmal Speicher.
- Optimierter Down- und Upload, da nur die Schichten geladen werden, die nicht bereits auf der Zielmaschine existieren.
- Bei Änderungen einer Schicht wird diese und alle darauf basierenden Schichten neu gebaut.

![Docker Images — Schichten](images/layer-reuse.png)

### Notizen

Der schichtenweise Aufbau resultiert in wichtigen Vorteilen zur Erstellung und zum
Bezug neuer Docker Images. Ein großer Vorteil ist, dass jede Schicht nur einmal
gespeichert wird. Das heißt, dass wenn sich Docker Images vom Aufbau her gleichen,
ihre Schichten nur einmal abgelegt werden. Zur Überprüfung ob die Schichten identisch
sind wird deren Prüfsumme verglichen. Die Prüfsumme bezieht sich hierbei auf den
Ausgangszustand, sowie die durchgeführten Änderungen. Zudem wird der Bauprozess
durch die Schichtenbildung optimiert da nur jene Schichten neu gebaut werden, deren
Prüfsummen sich verändert haben. Die Ablage der bereits gebauten Schichten wird im
Rahmen des Bauprozesses auch als Build-Cache bezeichnet. Ein weiterer Vorteil, der aus
dem geschichteten Aufbau entsteht ist, dass nicht das gesamte Docker Image hoch- oder
heruntergeladen werden muss, sondern nur jene Schichten, die nicht auf dem
Zielrechner existieren.

## Tags (Seite 21)

- Der Name (Tag) eines Docker Images ist in 4 Abschnitte gegliedert:
  1. Registry (optional)
  2. User/Organisation (Pflichtfeld)
  3. Imagename (Pflichtfeld)
  4. Version (optional)
- Wird kein Versionstag gesetzt, wird automatisch die Version ‚latest‘ verwendet.
- Tags sind Verweise auf ein konkretes Docker Image. Unterschiedliche Tags auf das gleiche Image verbrauchen keinen zusätzlichen Speicherplatz.

```text
https://hub.docker.com/plexinc/pms-docker:latest
Registry                  User     Image      Version
```

![Docker Image — Tags](images/tag-references.png)

### Notizen

Ein Docker Image wird mit seinem Tag referenziert. Das Tag eines Docker Images besteht
aus vier Abschnitten. Der erste Abschnitt trägt die Adresse der Docker Registry zu der
das Docker Image hochgeladen werden soll. Dieser Abschnitt ist optional, wird er nicht
gesetzt, wird die Docker Registry verwendet, die als Standard gesetzt ist. Der zweite
Abschnitt des Tags referenziert den registrierten Account des Users oder der
Organisation bei der Docker Registry unter dem das Image abgelegt werden soll. Der
dritte Abschnitt ist der tatsächliche Name des Docker Images. Der letzte Bestandteil des
Tags ist die Versionierung des Docker Images.

Die Versionsinformation ist optional, wird sie nicht gesetzt wird automatisch die Version
‚latest‘ gesetzt. Entgegen der wörtlichen Übersetzung steht ‚latest‘ hierbei nicht für die
aktuelle Version, sondern nur als Standardwert. Das heißt es ist auch möglich, dass ein
alter Versionsstand den Zusatz ‚latest‘ besitzt, da der Name ‚latest‘ nichts mit der
Aktualität des Images zu tun hat.

Bei Tags handelt es sich um Verweise auf den konkreten Versionsstand eines Docker
Images. Der Versionsstand eines Docker Images kann jedoch auch mehrere Tags tragen.

## Registry (Seite 22)

- Die Docker-Registry ist ein zentraler Ort zum Speichern und Verteilen von Docker Images.
- Ermöglicht die Umsetzung eines „image from the shelf“ Paradigma.
- Eine Docker Registry kann öffentlich (public), oder für einen geschlossenen Teilnehmerkreis (private), zugänglich sein.
- Die bekannteste public Registry ist https://hub.docker.com
  - Ist als Standard nach einer Installation gesetzt
  - Docker unterstützt mit einem eigenen Team die Aktualisierung der offiziellen Docker Images.
  - Offizielle Images tragen keine Usernamen im Tag.

### Notizen

Die Docker Registry ist ein zentraler Ablageort, der zum Speichern und Verteilen von
Docker Images dient. Hierdurch soll für Unternehmen das Paradigma eines „image from
the shelf“ umgesetzt werden. Das heißt ein Unternehmen, das ein Docker Image für eine
bestimmte Funktionalität sucht, soll ohne größere Hürden im Stande sein das
gewünschte Image direkt einzusetzen. Der Datentransfer zwischen dem Docker Deamon
und der Docker Registry basiert auf der Schichtenarchitektur, sodass nur die fehlende
Schichten übertragen werden. Bei der Docker Registry wird unterschieden ob diese
öffentlich zugänglich ist (public registry) oder nur für einen geschlossenen
Teilnehmerkreis (private registry), wie beispielsweise in Unternehmen.

Die bekannteste öffentliche Docker Registry ist Docker Hub. Diese Registry ist frei im
Internet zugänglich und als Standard nach der Installation von Docker gesetzt. Über
Docker Hub werden offizielle Images für bekannte Applikationen wie bspw. MySQL,
PostgreSQL, Spring, etc. angeboten. Hierzu unterhält Docker ein eigenes Team, das eng
mit den Projekten zusammenarbeitet und die Docker Images regelmäßig aktualisiert.
Offizielle Images zeichnen sich dadurch aus, dass sie keinen Namen des Users oder der
Organisation im Tag tragen.

## Hands-On: Recherche von Images (Seite 23)

1. Suche auf Docker Hub nach einem geeigneten Basisimages für eine Spring Anwendung
   - Offizielle Docker Images tragen haben keinen User im Tag.
   - Tags informieren über spezifische Konfigurationen.
   - Dokumentation über Startkonfiguration.

   https://hub.docker.com

2. Herunterladen des spezifischen Docker Images

   ```sh
   docker image pull openjdk:16-jdk-slim
   ```

3. Inspektion der einzelnen Schichten des Images

   ```sh
   docker image history openjdk:16-jdk-slim
   ```

## Dockerfile (Seite 24)

| Base-image | `FROM openjdk:8-jdk-alpine` |
| --- | --- |
| Anpassen von Abhängigkeiten & Konfiguration | `ENV demo.version=0.9` |
|  | `RUN mkdir app` |
|  | `WORKDIR app/` |
|  | `COPY target/*.jar app.jar` |
|  | `EXPOSE 8080` |
| Einstiegskommando | `CMD ["java","-jar","app.jar"]` |

- Ein Dockerfile ist eine einfache Textdatei mit dem Namen ‚Dockerfile‘, ohne Dateiendung.
- Der Bau eines neuen Docker Image wird gestartet via:

  ```sh
  docker image build -t imagetag .
  ```

- Jede Zeile ist eine eigene Instruktion, die eine Schicht erstellt.
- Der Aufbau eines Dockerfile ist dreigeteilt in: Baseimage, Konfigurationsanpassungen und dem Einstiegspunkt.
- Der Einstiegspunkt definiert, jenen Befehl, der beim Starten eines Docker Containers ausgeführt wird.

### Notizen

Eine andere Möglichkeit ein Docker Image zu erstellen ist das eigene Verfassen eines
eigenen Dockerfiles. Hierüber kann eine individuelle Ausführungsumgebung zum
Betreiben einer Anwendung konfiguriert werden. Das Dockerfile ist eine einfache
Textdatei, die den Namen ‚Dockerfile‘ ohne jegliche Dateiendung trägt. Ein Dockerfile
besteht generell aus drei zentralen Blöcken. Der erste Block benennt das Basisimage, auf
dessen Grundlage die Einrichtung durchgeführt wird. In der Regel werden hier schlanke
Linux Distributionen wie „apline linux“ (ca. 5 MB) eingesetzt um den digitalen
Fußabdruck des Docker Images so gering wie möglich zu halten. Der nächste Block
besteht aus den individuellen Anpassungen und der Übertragung des auszuführenden
Codes. Hierbei wird so oft wie möglich der Paketmanager der Linux Distribution
eingesetzt um Abhängigkeiten automatisch vom System handhaben zu lassen. Der letzte
Block eines Docker Images besteht aus dem Kommando, das beim Starten eines Docker
Containers ausgeführt wird.

## Dockerfile — FROM, ENV, RUN (Seite 25)

```dockerfile
FROM openjdk:8-jdk-alpine
ENV demo.version=0.9
RUN mkdir app
WORKDIR app/
COPY target/*.jar app.jar
EXPOSE 8080
CMD ["java","-jar","/app.jar"]
```

FROM

- Referenziert das Baseimage, das im Folgenden angepasst wird.
- Kein automatisches Update von Bibliotheken.

ENV

- Setzt Startwerte relevanter Umgebungsvariablen.
- Anpassung des Laufzeitverhaltens einer Anwendung.
- Kann zur Laufzeit überschrieben werden.

RUN

- Führt ein Kommando zur Bauzeit aus.
- Kommandos müssen vom Baseimage unterstützt werden.
- Anwendungen werden oft unter Nutzung des Paketmanagers installiert.

### Notizen

Nachdem wir uns zuvor den generellen Aufbau eines Docker Images angeschaut haben,
gehen wir im Folgenden detailliert auf die zu verwendende Befehlsstruktur ein. Der
Beginn jedes Dockerfiles bildet die Definition des Basisimages. Hierzu wird der Befehl
FROM eingesetzt, gefolgt vom konkreten Tag des eingesetzten Docker Image. Hierbei ist
es empfehlenswert, sehr detaillierte Tags zu verwenden, damit einem Außenstehenden
sofort klar ist auf welcher konkreten Version eines Images das Dockerfile basiert. Ferner
ist zu berücksichtigen, dass es keine automatische Aktualisierung der Docker Images
gibt, sondern die Aktualisierung manuell über den Austausch des verwendeten Tags
erfolgt.

Der Befehl ENV wird dazu eingesetzt, um Umgebungsvariablen in der
Ausführungsumgebung zu definieren. Umgebungsvariablen sind ein zentraler
Mechanismus um das Laufzeitverhalten einer Anwendung anzupassen, da sie von jedem
Betriebssystem unterstützt werden. So ist es beispielsweise möglich, Programmlogik
oder Versionsinformationen über Umgebungsvariablen zu beeinflussen. Ferner sind die
definierten Umgebungsvariablen nicht statisch, sondern können zur Laufzeit
überschrieben werden.

Mit dem Befehl RUN können Kommandos ausgeführt werden, wie wenn man direkt das
Betriebssystem verwenden würde. Unter Nutzung der RUN Befehle kann man somit
nötige Programme installieren oder Systemkonfigurationen, wie bspw. weitere Benutzer
hinzufügen.

## Dockerfile — WORKDIR, COPY, EXPOSE (Seite 26)

WORKDIR

- Setzt im Container das Ausgangsverzeichnis für alle folgenden Kommandos.
- Es entfällt die Wiederholung gleiche Verzeichnispräfix für das Ziel.

COPY

- Kopiert Dateien vom lokalen Verzeichnis in das Image.
- Unterstützung von Wildcards.

EXPOSE

- Zugriff zur Laufzeit kann nur über die aufgelisteten Ports erfolgen.
- Unabhängig von der Erreichbarkeit vom Host, die im Rahmen der publish Konfiguration definiert wird.

### Notizen

Das WORKDIR Kommando ist besonders hilfreich wenn es darum geht Dateien in das
gleiche Verzeichnis im Docker Container zu kopieren. Um Flüchtigkeitsfehler zu
vermeiden, die aus dem Copy-Paste von Verzeichnispfaden resultieren, kann man mit
dem WORKDIR Befehl ein Stammverzeichnis innerhalb des Containers setzten auf das
sich fortan alle Kommandos beziehen. Dadurch ist es nicht mehr nötig
übereinstimmende Verzeichnispfade für den Zielpfad bei den Kommandos mehrfach zu
wiederholen.

Der COPY Befehl dient dazu lokale Ressourcen in das Docker Image zu kopieren. Dies
bietet sich insbesondere für statische Binärdateien oder auszuführenden Programmcode
an. Hierbei ist zu beachten, dass der Befehl die Nutzung von Wildcards unterstützt.

Mit dem Befehl EXPOSE werden eingehende Portverbindungen für das spätere
Laufzeitverhalten definiert. Aus Sicherheitsgründen sind im Grundzustand
eingehende Netzwerkverbindungen auf einen Docker Container untersagt. Über
EXPOSE können nun jene Ports freigegeben werden für die eingehende
Verbindungen erlaubt sind. Wichtig hervorzuheben ist, dass dieses Kommando
unabhängig von der publish Option im Rahmen des docker container run Befehls
ist. Die publish Option definiert das Mapping von Container Ports auf eingehende
Portverbindungen des Hosts. Das EXPOSE Kommando gibt dagegen Ports für den
Container frei, sodass überhaupt eingehender Verkehr bei dem Container
zugelassen wird.

## Dockerfile — CMD (Seite 27)

CMD

- Startet den Applikationsprozess
- CMD kann zur Laufzeit überschrieben werden
- Zwei Formen:
  - Exec form: `["java","-jar","app.jar"]`
  - Shell form: `java –jar app.jar` Vorsicht!

### Notizen

Den Abschluss eines Dockerfile bildet der Befehl CMD. Dieser Befehl wird nicht
während der Bauzeit eines Docker Images ausgeführt, sondern es ist der erste
Befehl der nach dem Start eines Docker Containers ausgeführt wird. Der CMD
Befehl kann auf zweierlei Weise definiert werden. Bei der intuitiven „shell form“
wird der auszuführende Befehl, ähnlich zum RUN Befehl, in genau dem Format
spezifiziert wie er in die Kommandozeile eingegeben wird. Die abgewandelte
Form hierzu ist die „exec form“ Notation, bei der jedes Befehlsargument in einem
Arrayformat spezifiziert wird. Die beiden Notationsformen sind nicht
gleichbedeutend. Während bei der Exec Notation, der spezifizierte Befehl als
eigenständiger Prozess ausgeführt wird, ist der Befehl bei der shell Notation ein
Unterprozess der Shell. Das heißt wenn ein Angreifer aus dem
Anwendungsprozess ausbrechen würde, hätte er bei der exec Notation keine
weiteren Hilfsmittel, während er bei Verwendung der Shell Notation alle von der
Shell angebotenen Werkzeuge zur Verfügung hat.

## Überblick wichtiger Befehle (Seite 28)

|  |  |
| --- | --- |
| `docker image list` | Listet alle lokal vorhandenen Docker Images auf. |
| `docker image history hello-world` | Zeigt die einzelnen Schichten des hello-world Docker Images |
| `docker image tag alpine v1` | Erstellt den neuen Tag ‚v1‘ für das Docker Image, das den Tag ‚alpine‘ trägt |
| `docker image pull alpine` | Lädt das Image ‚alpine‘ von der Docker Registry herunter |
| `docker image build -t test .` | Erstellt ein neues Docker Image mit dem Tag ‚test‘ auf Grundlage des Dockerfiles im gleichen Verzeichnis |
| `docker image rm test` | Löscht das Docker Image ‚test‘ |

### Notizen

Die folgende Folie gibt einen Überblick über die wichtigsten Docker Befehle zum
Verwalten von Docker Images. Der erste Befehl ‚docker image list‘, gibt alle Docker
Images zurück die sich lokal auf dem Rechner befinden. Mit dem Befehl ‚docker image
history‘ gefolgt von dem Tag des entsprechenden Docker Images werden alle Schichten
des Images ausgegeben. Die Erstellung eines neuen Tags erfolgt mit dem Kommando
‚docker image tag‘. Hierbei ist zu beachten, dass ein neuer Tag erstellt wird, es wird aber
nicht der alte Tag gelöscht. Docker Images können mit dem Befehl ‚docker image pull‘
von der konfigurierten Docker Registry geladen werden. Um ein neues Docker Image auf
Grundlage eines Dockerfile zu erstellen wird der Befehl ‚docker image build -t
<ImageName> . ‘ ausgeführt. Dieser Befehl führt dazu, dass das Dockerfile, das im
gleichen Verzeichnis liegen muss, ausgewertet und ausgeführt wird um das neue Docker
Image zu erstellen. Bestehende Docker Images lassen sich mit dem Befehl ‚docker image
rm‘ gefolgt vom Imagenamen löschen.

## Spring Boot & Docker (Seite 29)

- Spring unterstützt die Nutzung von Umgebungsvariablen zur:
  - Nutzung unterschiedlicher Ressourcen und Endpunkte
  - Vermeidung sensibler Daten
  - Beschränkung des Funktionsumfangs
- Profile steuern die Sichtbarkeit ganzer Klassen sowie deren Konfiguration. Ferner wird die Properties Datei application-{profile}.properties gemäß des aktuellen Profiles gewählt.
- Die Umgebungsvariable Spring.profiles.active definiert das aktive Profil.
- Mit dem Befehl „mvn clean install“ wird ein self-contained (fat) Jar erzeugt, dass Abhängigkeiten minimiert.

Zugriff auf Umgebungsvariable

Standardwert

```java
@Value("${demo.version:0.0.1}")
private String version;
```

```java
@Value("${nameservers:1.1.1.1,8.8.8.8}")
private String[] nameservers;
```

Bean existiert nur für ‚dev‘ Profil

```java
@Service
@Profile("dev")
public class GreetingServic
```

### Notizen

Spring bietet für die Nutzung in Docker Container verschiedene Vorteile. Eine sehr
wichtige Eigenschaft ist die Möglichkeit auf Umgebungsvariablen leicht zuzugreifen und
mit ihnen tief in das Verhalten der Anwendung einzugreifen. Der Haupteinsatzzweck für
Umgebungsvariablen ist die Definition von Ressourcen und Web-Endpunkten
entsprechend der aktuellen Laufzeit. Oft werden beispielsweise in der Entwicklung
andere Endpunkte von Webservices verwendet als jene im produktiven Betrieb. Darüber
hinaus können Umgebungsvariablen dazu eingesetzt werden, dass sensitive Daten
(bspw. Passwörter) erst gar nicht generiert werden. Dies kann insbesondere sehr nützlich
sein, wenn Logdateien dauerhaft gespeichert werden. Abschließend können
Umgebungsvariablen in Spring auch zur Einschränkung des Funktionsumfangs eingesetzt
werden, sodass unterschiedliche Implementierungen für die Entwicklungsumgebung und
produktive Umgebung verwendet werden.

Darüber hinaus zeichnet sich Spring durch die Nutzung von Profilen aus. Profile steuern
die Sichtbarkeit und Konfiguration ganzer Java Klassen, sodass es möglich ist vollkommen
andere Klassen für die Implementierung eines Interfaces im produktiven Betrieb und in
der Entwicklung einzusetzen. Ferner wird automatisch gemäß dem aktuell gewählten
Profil die entsprechende Properties Datei gemäß dem Schema application-
{profile}.properties ausgewählt. Das aktuelle Profil wird durch die Umgebungsvariable
Spring.profiles.active gesetzt.

Der Befehl ‚mvn clean install‘ kann dazu eingesetzt werden, dass mit Spring ein
sogenanntes Fat-Jar erzeugt wird, in das alle internen und externen Abhängigkeiten
integriert sind. Anschließend kann diese Jar Datei ohne weitere Abhängigkeiten
ausgeführt werden.

## Hands-On (Seite 30)

|  |  |
| --- | --- |
| `cd Spring2Docker` | Wechselt in das Projektverzeichnis auf dem Host |
| `mvn clean install` | Veranlasst Spring Boot eine Jar Datei zu bauen |
| `docker image build -t test .` | Baut ein neues Docker Image mit dem Tag ‚test‘ basierend auf dem Dockerfile |
| `docker container run -d -p 80:8080 test` | Erstellt einen neuen Docker Container und führt diesen aus. Port 80 des Host wird auf Port 8080 im Container weitergeleitet |

## Hands-On (Seite 31)

|  |  |
| --- | --- |
| Browser: http://localhost:80 | Führt eine HTTP-Anfrage auf dem Host unter Port 80 aus. Als Antwort kommt „ Herzlich Willkommen zur Veranstaltung Cloud Computing“ zurück. |
| `docker container list` | Gibt eine Liste mit allen laufenden Containern aus. |
| `docker container logs ce5` | Zeigt die Logs für die ContainerId, welche im letzten Schritt ermittelt wurde, bspw. ce5 |

```text
$ docker container list
CONTAINER ID   IMAGE   COMMAND               CREATED          STATUS          PORTS                  NAMES
ce5ecae6ccb7   test    "java -jar app.jar"   23 minutes ago   Up 23 minutes   0.0.0.0:80->8080/tcp   reverent_turing
```

Quelle: cloud-computing/origin/WDS125 - Cloud Computing (SCA)/05 Docker/3-Docker/3-Docker.pdf, Seiten 18–31

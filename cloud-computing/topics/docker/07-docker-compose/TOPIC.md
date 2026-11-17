# 6. Docker Compose

Starten von „Container-Gruppen“

## Motivation (Seite 64)

- Die bisherige Konfiguration von Volumes und Networks erfordert viel manuellen Aufwand und das Setzen von Optionen.
- Des weiteren müssen die Container einzeln von Hand gestartet werden, was die Automatisierbarkeit erschwert.
- Docker Compose verwendet eine deklarative Konfigurationsdatei, mit der komplexe Umgebungen einfach beschrieben und gestartet werden können.

### Notizen

Die Verwaltung komplexer Containerumgebungen mit mehreren Services erfordert in
der Standard-Docker-CLI viele manuelle Schritte. Jede Komponente – etwa Anwendung,
Datenbank und Backend – muss einzeln gestartet, verknüpft und mit den passenden
Volumes und Netzwerken konfiguriert werden. Dieses Vorgehen ist fehleranfällig, schwer
reproduzierbar und erschwert die Automatisierung, insbesondere in Entwicklungs- und
Testumgebungen.

Docker Compose adressiert genau dieses Problem. Es führt einen deklarativen Ansatz für
Containerkonfigurationen ein: Statt Container, Netzwerke und Volumes über einzelne
Befehle (docker run, docker network create, docker volume create) zu definieren,
werden alle Komponenten in einer zentralen Datei (compose.yaml) beschrieben. Diese
Datei legt fest, welche Services existieren, wie sie miteinander verbunden sind und
welche Ressourcen sie nutzen.

Der große Vorteil besteht darin, dass eine vollständige, mehrschichtige Umgebung mit
einem einzigen Befehl („docker compose up “) gestartet werden kann. Damit wird aus
einer Sammlung einzelner Container eine orchestrierte Anwendung mit klar definierten
Abhängigkeiten.

## YAML (Seite 65)

- YAML (YAML Ain‘t another Markup Language) ein menschenlesbares Datenserialisierungsformat.
- Struktur wird über Leerzeichen abgebildet
- Zuweisungen erfolgen durch Schlüssel-Wert Notation (vgl. JSON)
- Zeilenkommentare werden mit einem # gekennzeichnet

```yaml
DHBW:
  Ravensburg:
    Studierende: 2223
    Mitarbeiter: 190
  Heidenheim:
    Studierende: 2413
    Mitarbeiter: 176
```

### Notizen

Das YAML-Format bildet die Grundlage für die Konfigurationsdateien von Docker
Compose. Es handelt sich um ein menschenlesbares Datenserialisierungsformat, das
darauf ausgelegt ist, komplexe Strukturen übersichtlich und einfach editierbar
darzustellen. Der Name YAML steht für “YAML Ain’t Another Markup Language” und
betont damit, dass es – anders als XML oder HTML – kein Auszeichnungs-, sondern ein
reines Datenbeschreibungsformat ist.

Die Struktur einer YAML-Datei basiert auf Einrückungen mittels Leerzeichen statt
Klammern oder Kommata. Diese Formatierung spiegelt hierarchische Beziehungen
zwischen Elementen wider. Damit ist YAML besonders geeignet für
Konfigurationsdateien, in denen verschachtelte Objekte oder abhängige Strukturen – wie
Services, Volumes und Netzwerke – übersichtlich dargestellt werden müssen.

Durch diese klare, leicht lesbare Syntax können Konfigurationen auch ohne
Programmierkenntnisse verstanden und angepasst werden. Kommentare beginnen mit
dem Zeichen # und dienen zur Dokumentation oder zum temporären Deaktivieren von
Einträgen.

## YAML (Seite 66)

- YAML unterstützt die primitiven Datentypen: String, Int, Double und Boolean.
- Die Datentypen werden implizit abgeleitet, basierend auf dem Format des Wertes.
- Strings können auch mit Anführungszeichen oder Hochkommas deklariert werden.
- YAML respektiert die Groß-Kleinschreibung (Case-Sensitive)

```yaml
Stunden: 55
Programmierung: true
Raum: Labor
```

### Notizen

YAML unterscheidet sich von klassischen Programmiersprachen oder Datenformaten wie
JSON dadurch, dass Datentypen implizit abgeleitet werden. Das bedeutet, dass der Typ
eines Wertes automatisch anhand seines Formats erkannt wird – ohne dass eine
explizite Typdeklaration erforderlich ist. Hierbei werden primitive Datentypen wie String
(z. B. "Labor“), Int (z. B. „55“), Double (z. B. „3.14“) und Boolean (z. B. „true“).

Wichtig ist außerdem, dass Strings optional in Anführungszeichen gesetzt werden
können – das ist nur notwendig, wenn Sonderzeichen, Leerzeichen oder spezielle
Schlüsselwörter enthalten sind (z. B. "true" als Text statt als boolescher Wert). YAML
unterscheidet außerdem strikt zwischen Groß- und Kleinschreibung (case-sensitive).

## YAML (Seite 67)

- Als erweiterte Datentypen unterscheidet YAML Objekte, Dictionaries und Listen.
- Die Zuordnung von Attributen zu Objekten geschieht über die Einrückung.
- Die Einträge in einem Dictionary werden nicht geordnet abgelegt und können über ihren Namen angesprochen werden (bspw. DHBW[Heidenheim])
- Bei Listen werden die Werte in geordneter Reihenfolge gespeichert.

```yaml
DHBW:
  Ravensburg:
    Studierende: 2223
    Mitarbeiter: 190
  Heidenheim:
    Studierende: 2413
    Mitarbeiter: 176
```

„DHBW“ ist hier ein Dictionary bestehend aus den zwei Einträgen „Ravensburg“ und „Heidenheim“

```yaml
Studiengänge:
  - Wirtschaftsinformatik
  - Data Science
  - Elektrotechnik
```

### Notizen

Über die primitiven Datentypen hinaus erlaubt YAML die Modellierung komplexer
Datenstrukturen, die in Docker Compose zur Beschreibung verschachtelter
Konfigurationen (z. B. Services, Netzwerke und Volumes) notwendig sind.

Hierzu werden die folgenden drei Strukturtypen unterschieden: Objekte, Dictionaries
(Schlüssel-Wert-Zuordnungen) und Listen (geordnete Sequenzen).

Bei YAML erfolgt die Strukturierung der Objekte durch Einrückung. Jede zusätzliche
Ebene der Einrückung repräsentiert eine weitere logische Verschachtelung.

Dictionaries (vergleichbar mit Maps oder JSON-Objekten) speichern Schlüssel-Wert-
Paare. Die Einträge sind nicht geordnet und können über ihre Schlüssel angesprochen
werden.

Listen (eingeleitet durch Bindestriche) speichern Werte in einer geordneten
Reihenfolge.

## Überblick (Seite 68)

```yaml
services:
 web:
  image: nginx
  ports:
   - "8080:80"
  networks:
   - mynet

volumes:
 psql:

networks:
 mynet:
```

- Das docker-compose File ist eine YAML-Textdatei mit dem Namen ‚compose.yaml‘.
- Die darin beschriebene Konfiguration wird mit dem Befehl docker compose up hergestellt.
- Seit 2020 ist in der obersten Zeile keine Versionsinformation mehr nötig.
- Die docker-compose Datei ist in drei Abschnitte gegliedert: services, volumes, networks

### Notizen

Eine compose.yaml-Datei beschreibt die Struktur und Konfiguration einer
mehrcontainerbasierten Docker-Anwendung in Form von Services, Volumes und
Networks. Sie ist eine YAML-Textdatei mit dem Standardnamen compose.yaml und dient
als zentrale Steuerdatei, um mehrere Container gemeinsam und konsistent zu starten.

In aktuellen Compose-Dateien ist keine version:-Angabe mehr erforderlich. Docker
erkennt automatisch die Syntax basierend auf den verwendeten Features, was die Datei
übersichtlicher macht und Fehlerquellen reduziert.

Die Datei ist in drei Hauptabschnitte gegliedert:

services: Hier werden die einzelnen Container definiert. Jeder Service beschreibt ein
Image (z. B. nginx), Portfreigaben, Umgebungsvariablen, Netzwerke und gegebenenfalls
Abhängigkeiten zu anderen Containern. Der Abschnitt ist der zentrale Bestandteil der
Compose-Datei, da hier die eigentliche Laufzeitlogik der Anwendung festgelegt wird.

volumes: Hier werden persistente Datenspeicher beschrieben, die über
Containerneustarts hinweg bestehen bleiben. So können Datenbanken, Logs oder
Benutzerdateien dauerhaft erhalten werden.

networks: Hier wird festgelegt, wie die Container untereinander kommunizieren können.
Netzwerke ermöglichen es, Services voneinander zu isolieren oder gezielt miteinander
zu verbinden, ohne dass sie direkt von außen erreichbar sind.

## Überblick (Seite 69)

```yaml
services:
 web:
  image: nginx
  ports:
   - "8080:80"
  environment:
   Log_Level: Info
  networks:
   - mynet

volumes:
 psql:

networks:
 mynet:
```

- Ein Service steht bei Docker-Compose für die Startkonfiguration eines Docker-Containers (bspw. Name, Image, Ports, Volumes, etc.)
- Unter Services werden alle Startkonfigurationen definiert, die zusammen eine Anwendung bilden.
- Der servicename kann als Hostname für die Intra-Container Kommunikation verwendet werden.
- Die Umgebungsvariablen werden im Dictionary environment aufgelistet.

### Notizen

Der Abschnitt services: bildet das Herzstück jeder compose.yaml-Datei. Hier wird
definiert, welche Container gestartet werden, wie sie konfiguriert sind und wie sie
miteinander interagieren Ein Service beschreibt hierbei die Startkonfiguration eines
Containers. Jeder Service steht dabei für eine klar abgegrenzte
Anwendungskomponente, etwa eine Web-App, eine Datenbank oder einen Cache. In der
Compose-Datei werden alle Services gemeinsam definiert, die zusammen ein
Gesamtsystem bilden.

Jeder Service-Eintrag enthält die zentralen Laufzeitparameter des zugehörigen
Containers:

image: legt das zu verwendende Container-Image fest (z. B. nginx oder postgres).

ports: definiert die Portzuordnungen zwischen Host und Container, um externe Zugriffe
zu ermöglichen.

environment: enthält Umgebungsvariablen, die innerhalb des Containers gesetzt
werden (z. B. Log_Level: Info).

networks: ordnet den Service einem oder mehreren Netzwerken zu, um die
Kommunikation zwischen Containern zu ermöglichen.

volumes (optional): ermöglicht die Einbindung persistenter Datenspeicher.

Der Servicename fungiert innerhalb des Compose-Netzwerks automatisch als
Hostname. Dadurch können Container über einfache Namensauflösung miteinander
kommunizieren – z. B. kann ein web-Service eine Datenbank über postgres:5432
ansprechen, ohne IP-Adressen kennen zu müssen.

## Überblick (Seite 70)

- Die benötigten Volumes werden im Abschnitt volumes, die verwendeten Netzwerke im Abschnitt networks definiert.
- Bei YAML kann ein Schlüssel auch ohne Wert stehen, hierbei werden dann die Standardwerte verwendet.
- Standard-Volume mit Namen „psql“
- Standard-Konfiguration (bridge) für Netzwerk „mynet“.

### Notizen

In einer compose.yaml-Datei werden neben den eigentlichen Containern (services) auch
die zugehörige Datenhaltung (volumes) und die Kommunikationsstruktur (networks)
definiert. Beide Abschnitte stehen auf oberster YAML-Ebene und bilden die Grundlage
für eine saubere Trennung von Code, Daten und Infrastruktur.

Der Abschnitt volumes: beschreibt persistente Speicherbereiche, die unabhängig vom
Lebenszyklus eines Containers existieren. Diese Volumes können gleichzeitig von
mehreren Containern genutzt werden – ein zentrales Konzept in Docker, um Daten
gemeinsam verfügbar zu machen, etwa bei gemeinsam genutzten Datenbanken,
Logverzeichnissen oder Konfigurationsdateien. Im Beispiel wird ein Volume mit dem
Namen psql definiert.

Der Abschnitt networks: legt fest, über welche logischen Netzwerke die Container
miteinander kommunizieren können. Das hier definierte Netzwerk mynet nutzt ebenfalls
die Standardkonfiguration, was bedeutet, dass ein lokales Bridge-Netzwerk erstellt wird.
Innerhalb dieses Netzwerks können Container miteinander kommunizieren, ohne dass
sie von außen erreichbar sind.

## Hands On (Seite 71)

- Der aktuelle Ordner wird als Projektname verwendet
- Erst wird das Netzwerk, dann das Volume und zuletzt der Container erstellt.
- Der Befehl docker compose down löscht den Container und das Netzwerk, aber nicht das Volume.
- Jeder Service bekommt eine eigene Farbe zugewiesen

![Docker Compose — Hands On](images/compose-up-output.png)

### Notizen

Der Befehl docker compose up startet die in der compose.yaml-Datei definierte
Anwendung. Dabei werden alle abhängigen Ressourcen in der richtigen Reihenfolge
erzeugt: zuerst das Netzwerk, anschließend die Volumes und schließlich die Container.
Als Projektname verwendet Compose standardmäßig den aktuellen Ordnernamen,
wodurch die erzeugten Ressourcen eindeutig gruppiert werden. So entsteht eine
logische Zuordnung von Netzwerk, Volume und Container zu einem Projekt, ohne dass
Namenskonflikte mit anderen Compose-Projekten auftreten.

Der Terminalauszug zeigt, dass Docker Compose die einzelnen Schritte transparent
protokolliert. Jede Ressource (Netzwerk, Volume, Container) erhält den Status Created,
bevor der Container gestartet und die Logausgabe sichtbar wird. Durch diese
Automatisierung werden komplexe Multi-Container-Umgebungen mit einem einzigen
Befehl reproduzierbar bereitgestellt.

Der zugehörige Befehl docker compose down entfernt anschließend Container und
Netzwerke, nicht jedoch die Volumes. Dieses Verhalten ist bewusst so gewählt, da
Volumes persistente Daten enthalten, die über Neustarts hinweg erhalten bleiben sollen
– beispielsweise Datenbanken.

Zur besseren Lesbarkeit weist Docker Compose jedem Service eine eigene Farbe in der
Logausgabe zu. Dadurch lassen sich parallele Logs verschiedener Container visuell
unterscheiden, was die Fehlersuche und Nachvollziehbarkeit deutlich erleichtert.

## Image Building (Seite 72)

```yaml
services:
 proxy:
  build:
   context: .
   dockerfile: ngix.Dockerfile
  ports:
   - "80:80"
 web:
  image: httpd
  volumes:
   - ./html:/usr/local/apache2/htdocs/
```

- Beim Image Building werden neue Docker Images im Rahmen von „docker compose up“ gebaut.
- Hierzu wird das Dockerfile und der Ordner für den Bauprozess spezifiziert. Das gebaute Image bekommt den Tag {foldername}_{servicename}_{nr}
- Mittels --build werden die Images vor dem Start neu gebaut, ansonsten wird das vorhandene Image verwendet.
- Neu gebaute Images werden mit dem Zusatz --rmi=local beim docker compose down Befehl gelöscht.

### Notizen

Beim Start einer Anwendung mit docker compose up können nicht nur Container aus
bestehenden Images erzeugt, sondern auch eigene Images automatisch gebaut werden.
Docker Compose integriert damit den gesamten Build-Prozess direkt in den
Anwendungsstart und unterstützt sowohl vorgefertigte Images (image: …) als auch selbst
definierte Builds (build: …).

Im Abschnitt build: wird das Verzeichnis angegeben, in dem sich das Dockerfile befindet,
sowie optional der Name des Dockerfiles selbst. Im gezeigten Beispiel wird für den
Service proxy im aktuellen Ordner (context: .) das Dockerfile ngix.Dockerfile verwendet.
Docker Compose erstellt daraus ein neues Image, das nach dem Schema
{foldername}{servicename}{nr} benannt wird – eine automatische, projektbezogene
Namenskonvention, die Kollisionen zwischen unterschiedlichen Projekten vermeidet.

Images werden nur dann neu gebaut, wenn sie nicht im lokalen Cache vorhanden sind.
Um den Build explizit zu erzwingen, kann die Option --build verwendet werden (docker
compose up --build). Dadurch wird der Build vor dem Start erneut ausgeführt – nützlich,
wenn sich die Build-Umgebung oder das Basisimages geändert haben.

Über den Befehl docker compose down --rmi local lassen sich alle im aktuellen
Projektkontext erstellten Images wieder entfernen. Diese Option ist hilfreich, um
Entwicklungsumgebungen aufzuräumen und Speicherplatz freizugeben, ohne Volumes
oder Netzwerke zu löschen.

## Überblick wichtiger Befehle (Seite 73)

|  |  |
| --- | --- |
| `docker compose up` | Startet die in compose.yaml definierten Container, Netzwerke und Volumes. Nutzt bereits vorhandene Images, falls verfügbar. |
| `docker compose up --build` | Gleich wie oben, nur dass Neubauen der Images erzwungen wird auch wenn die Images bereits existieren. |
| `docker compose down` | Beendet alle laufenden Container und entfernt zugehörige Netzwerke, Volumes werden beibehalten. |
| `docker compose down --rmi=local` | Gleich wie oben, nur dass zusätzlich lokal gebaute Images gelöscht werden. |

### Notizen

Die dargestellten Befehle bilden den zentralen Arbeitszyklus in Docker Compose ab:

Mit docker compose up wird die im YAML-File definierte Umgebung gestartet. Dabei
werden alle Services, Netzwerke und Volumes erstellt und die Container in der richtigen
Reihenfolge gestartet. Existieren zugehörige Images bereits, werden diese
wiederverwendet, was den Startprozess beschleunigt.

Die Variante docker compose up --build erzwingt einen Neuaufbau der Images selbst
wenn die Images bereits existieren.

Mit docker compose down wird die gesamte Umgebung kontrolliert heruntergefahren.
Dabei werden Container, Netzwerke und temporäre Ressourcen entfernt, während
Volumes standardmäßig bestehen bleiben, um persistente Daten zu bewahren.

Der Befehl docker compose down --rmi local erweitert diesen Prozess, indem zusätzlich
alle lokal gebauten Images gelöscht werden. Das ist insbesondere in Entwicklungs- oder
Testumgebungen nützlich, um Speicherplatz freizugeben und saubere Neuaufbauten zu
erzwingen.

Quelle: cloud-computing/origin/WDS125 - Cloud Computing (SCA)/05 Docker/3-Docker/3-Docker.pdf, Seiten 64–73

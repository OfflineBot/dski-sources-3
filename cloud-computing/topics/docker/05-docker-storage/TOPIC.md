# 4. Docker Storage

Speichern von Daten in Docker

## Motivation (Seite 44)

Docker Container

- Änderungen am Container sind flüchtig (vgl. r/w Layer)
- Immutable Infrastruktur

Datenbank

- Daten müssen nach Neustart der Serverinfrastruktur da sein.
- „Persistent Data“

Separation of Concerns (Trennung von Code und Daten)

### Notizen

Docker Container unterscheiden sich grundlegend zu persistenten Datenspeichern wie
Datenbanken:

Container folgen dem Paradigma der immutable infrastructure – sie sind also
unveränderlich in dem Sinne, dass jede Änderung innerhalb eines Containers (z. B. durch
Schreiboperationen) nur in einer temporären, sogenannten r/w Layer abgelegt wird.
Diese Schicht ist ephemeral (flüchtig), d. h. sie geht nach dem Löschen des Containers
verloren.

Im Gegensatz dazu benötigen Datenbanken persistente Datenhaltung. Daten müssen
auch nach einem Neustart oder nach dem Austausch der Serverinfrastruktur weiterhin
verfügbar sein. Sie sind somit ein klassisches Beispiel für persistent data.

Docker Storage ermöglichen genau diese Trennung, indem sie Daten außerhalb der
ephemeral Container-Schicht ablegen. Damit bleibt die Anwendung immutable, während
ihre Daten dauerhaft und unabhängig vom Lebenszyklus des Containers gespeichert
werden können.

## Docker Volumes (Seite 45)

- Ein Docker Volume ist ein persistenter Speicher außerhalb des flüchtigen Docker Containers.
- Alle Veränderungen in einem spezifizierten Verzeichnis des Containers werden in das Volume geschrieben.
- Das Verzeichnis, das in ein Volume gespeichert wird kann im Dockerfile spezifiziert werden Bspw. VOLUME /var/lib/mysql
- Im Rahmen des docker container run Befehls wird ein Volume mit dem Container verknüpft.

### Notizen

Ein Docker Volume stellt einen externen Speicherbereich dar, der außerhalb des
Lebenszyklus eines Containers liegt. Dadurch wird die Trennung zwischen Code
(Container) und Daten (Volume) technisch umgesetzt. Wenn ein Container gelöscht oder
neu erstellt wird, bleiben die in einem Volume gespeicherten Daten bestehen.

Wird ein Verzeichnis innerhalb des Dockerfiles als Volume deklariert, so werden alle
Änderungen in diesem Verzeichnis nicht mehr in den flüchtigen r/w Layer geschrieben,
sondern in das Volume. Dieses Volume kann dabei lokal auf dem Hostsystem oder auf
einem entfernten Speicher liegen.

Im Dockerfile wird dies bspw. mit dem Befehl VOLUME /var/lib/mysql definiert.
Beim Start eines Containers wird das Volume eingebunden (gemountet). Somit bleibt die
Anwendungslogik immutable, während die Daten persistent gespeichert werden.

## Überblick Docker Volumes (Seite 46)

Docker Volume

`myDB`

Dockerfile

```dockerfile
…
VOLUME /var/lib/mysql
…
```

Docker Container

```sh
docker container run –v myDB:/var/lib/mysql mysql:8
```

### Notizen

Die folgende Folie gibt einen Überblick über das Zusammenspiel von Dockerfile, Docker
Container und Data Volume:

Das Volume mit dem Namen myDB repräsentiert einen persistenten Speicherbereich,
der außerhalb der flüchtigen Containerstruktur liegt.

Im Dockerfile wird bereits beim Bau eines Images festgelegt, welche Verzeichnisse als
Volume behandelt werden sollen. Dies geschieht über den Befehl „Volume“ gefolgt vom
Verzeichnispfad, der in das Data Volume geschrieben werden soll.

Bei der Ausführung des Containers erfolgt die Verknüpfung des logischen Volumes mit
dem Containerverzeichnis über den Parameter -v. Der Befehl: docker container run -v
myDB:/var/lib/mysql mysql:8 bindet das Volume myDB an den Container an.
Änderungen innerhalb des Verzeichnisses /var/lib/mysql werden fortan im Volume
gespeichert und bleiben somit persistent.

## Überblick wichtiger Befehle zu Docker Volumes (Seite 47)

|  |  |
| --- | --- |
| `docker volume create myDB` | Erstellt ein neues Volume auf dem Host |
| `docker volume ls` | Listet alle auf einem Host gespeicherten Volumes auf |
| `docker volume inspect myDB` | Gibt Details zum Volume „myDB“ aus. Beachte: Auf Windows und MacOS kann auf die Volume Verzeichnisse nicht einfach zugegriffen werden, da Docker mittels VM ausgeführt wird. |
| `docker volume rm myDB` | Löscht das Volume mit dem Namen ‚myDB‘. |
| `docker volume prune` | Löscht alle nicht verwendeten Volumes. |

### Notizen

Die folgende Übersicht gibt einen Überblick über die wichtigsten Befehle zum Verwalten
von Docker Volumes:

Der Befehl docker volume ls listet alle auf dem Docker-Host gespeicherten Volumes auf.
Er ist insbesondere hilfreich, um einen Überblick über vorhandene Volumes zu erhalten
und ungenutzte Volumes zu identifizieren.

Mit dem Befehl docker volume inspect myDB lassen sich detaillierte Informationen zu
einem spezifischen Volume abrufen, etwa Speicherort, Mount-Pfade und Nutzung durch
Container.

Der Befehl docker volume rm myDB wird das Volume myDB vom Hostsystem entfernt.

Der Befehl docker volume prune löscht alle nicht verwendeten Volumes auf dem Host.

## Bind Mounts (Seite 48)

- Bind Mounts sind eine Verknüpfung zwischen einer Datei oder einem Verzeichnis des Hosts und dem Container.
- Bind Mounts werden nicht im Dockerfile sondern ausschließlich im docker container run Befehl spezifiziert.
- Hierbei wird erst der Pfad auf dem Host zum zu verknüpfenden Verzeichnis und dann der korrespondierende Endpunkt im Container spezifiziert.

### Notizen

Während Docker Volumes von Docker verwaltet werden, ermöglichen Bind Mounts eine
direkte Kopplung an das Dateisystem des Hosts, was sie flexibler, aber auch
fehleranfälliger macht. Bind Mounts verknüpfen ein Verzeichnis oder eine Datei des
Hostsystems mit einem Pfad innerhalb des Containers. Dadurch können Daten in
Echtzeit zwischen Host und Container synchronisiert werden. Änderungen am Host
spiegeln sich sofort im Container wider und umgekehrt. Dies ist insbesondere in der
Entwicklungsphase von Vorteil, da Quellcode, Konfigurationsdateien oder Logfiles
während der Laufzeit editiert und sofort sichtbar werden. Im Gegensatz zu Volumes
werden Bind Mounts nicht im Dockerfile definiert, sondern ausschließlich beim Starten
des Containers

## Bind Mounts (Seite 49)

Data Volume

`/home/student/myproject`

Docker Container

```sh
docker container run –v /home/student/myproject:/app/myproject mytest
```

### Notizen

Diese Folie verdeutlicht die konkrete Umsetzung von Bind Mounts anhand eines
praktischen Beispiels. Konkret wird hier ein lokales Verzeichnis des Hosts
(/home/student/myproject) mit einem Verzeichnis im Container (/app/myproject)
verknüpft. Dadurch entsteht eine direkte Kopplung zwischen Host-Dateisystem und
Container, bei der Änderungen auf einer Seite unmittelbar auf die andere übertragen
werden.

Diese Vorgehensweise ist besonders in Entwicklungsumgebungen nützlich, z. B. wenn
Quellcode oder Konfigurationsdateien auf dem Host bearbeitet und sofort im Container
sichtbar werden sollen.

Die Verknüpfung erfolgt über den Befehl: docker container run -v
/home/student/myproject:/app/myproject

Die Option -v steht für volume und definiert hier ein Bind Mount, bestehend aus zwei
Pfadangaben:

Host-Pfad: /home/student/myproject → verweist auf das lokale Verzeichnis auf dem
Hostsystem.

Container-Pfad: /app/myproject → definiert den Mount-Punkt im Container.

Quelle: cloud-computing/origin/WDS125 - Cloud Computing (SCA)/05 Docker/3-Docker/3-Docker.pdf, Seiten 44–49

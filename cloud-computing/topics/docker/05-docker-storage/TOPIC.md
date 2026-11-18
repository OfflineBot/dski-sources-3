# 4. Docker Storage

Speichern von Daten in Docker

## Motivation

Docker Container

- Änderungen am Container sind flüchtig (vgl. r/w Layer)
- Immutable Infrastruktur

Datenbank

- Daten müssen nach Neustart der Serverinfrastruktur da sein.
- „Persistent Data“

Separation of Concerns (Trennung von Code und Daten)

### Notizen

- Docker Container unterscheiden sich grundlegend zu persistenten Datenspeichern wie Datenbanken.
- Container folgen dem Paradigma der immutable infrastructure: Sie sind unveränderlich in dem Sinne, dass jede Änderung innerhalb eines Containers (z. B. durch Schreiboperationen) nur in einer temporären, sogenannten r/w Layer abgelegt wird. Diese Schicht ist ephemeral (flüchtig), d. h. sie geht nach dem Löschen des Containers verloren.
- Datenbanken benötigen persistente Datenhaltung: Daten müssen auch nach einem Neustart oder nach dem Austausch der Serverinfrastruktur weiterhin verfügbar sein. Sie sind ein klassisches Beispiel für persistent data.
- Docker Storage ermöglichen genau diese Trennung, indem sie Daten außerhalb der ephemeral Container-Schicht ablegen. Damit bleibt die Anwendung immutable, während ihre Daten dauerhaft und unabhängig vom Lebenszyklus des Containers gespeichert werden können.

## Docker Volumes

- Ein Docker Volume ist ein persistenter Speicher außerhalb des flüchtigen Docker Containers.
- Alle Veränderungen in einem spezifizierten Verzeichnis des Containers werden in das Volume geschrieben.
- Das Verzeichnis, das in ein Volume gespeichert wird kann im Dockerfile spezifiziert werden Bspw. `VOLUME /var/lib/mysql`
- Im Rahmen des `docker container run` Befehls wird ein Volume mit dem Container verknüpft.

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
docker container run -v myDB:/var/lib/mysql mysql:8
```

### Notizen

- Ein Docker Volume liegt außerhalb des Lebenszyklus eines Containers. Dadurch wird die Trennung zwischen Code (Container) und Daten (Volume) technisch umgesetzt: Wenn ein Container gelöscht oder neu erstellt wird, bleiben die in einem Volume gespeicherten Daten bestehen.
- Wird ein Verzeichnis innerhalb des Dockerfiles als Volume deklariert, werden alle Änderungen in diesem Verzeichnis nicht mehr in den flüchtigen r/w Layer geschrieben, sondern in das Volume. Dieses Volume kann lokal auf dem Hostsystem oder auf einem entfernten Speicher liegen.
- Im Dockerfile wird bereits beim Bau eines Images festgelegt, welche Verzeichnisse als Volume behandelt werden sollen: über den Befehl „Volume“ gefolgt vom Verzeichnispfad, der in das Data Volume geschrieben werden soll.
- Beim Start eines Containers wird das Volume eingebunden (gemountet). Die Verknüpfung des logischen Volumes mit dem Containerverzeichnis erfolgt über den Parameter -v.
- `docker container run -v myDB:/var/lib/mysql mysql:8` bindet das Volume myDB an den Container an. Änderungen innerhalb des Verzeichnisses /var/lib/mysql werden fortan im Volume gespeichert und bleiben somit persistent.

## Überblick wichtiger Befehle zu Docker Volumes

|  |  |
| --- | --- |
| `docker volume create myDB` | Erstellt ein neues Volume auf dem Host |
| `docker volume ls` | Listet alle auf einem Host gespeicherten Volumes auf |
| `docker volume inspect myDB` | Gibt Details zum Volume „myDB“ aus. Beachte: Auf Windows und MacOS kann auf die Volume Verzeichnisse nicht einfach zugegriffen werden, da Docker mittels VM ausgeführt wird. |
| `docker volume rm myDB` | Löscht das Volume mit dem Namen ‚myDB‘. |
| `docker volume prune` | Löscht alle nicht verwendeten Volumes. |

### Notizen

- `docker volume ls` ist insbesondere hilfreich, um einen Überblick über vorhandene Volumes zu erhalten und ungenutzte Volumes zu identifizieren.
- `docker volume inspect myDB`: detaillierte Informationen zu einem spezifischen Volume, etwa Speicherort, Mount-Pfade und Nutzung durch Container.

## Bind Mounts

- Bind Mounts sind eine Verknüpfung zwischen einer Datei oder einem Verzeichnis des Hosts und dem Container.
- Bind Mounts werden nicht im Dockerfile sondern ausschließlich im `docker container run` Befehl spezifiziert.
- Hierbei wird erst der Pfad auf dem Host zum zu verknüpfenden Verzeichnis und dann der korrespondierende Endpunkt im Container spezifiziert.

Data Volume

`/home/student/myproject`

Docker Container

```sh
docker container run -v /home/student/myproject:/app/myproject mytest
```

### Notizen

- Docker Volumes werden von Docker verwaltet. Bind Mounts ermöglichen dagegen eine direkte Kopplung an das Dateisystem des Hosts, was sie flexibler, aber auch fehleranfälliger macht.
- Daten können in Echtzeit zwischen Host und Container synchronisiert werden: Änderungen am Host spiegeln sich sofort im Container wider und umgekehrt.
- Insbesondere in der Entwicklungsphase (in Entwicklungsumgebungen) von Vorteil, da Quellcode, Konfigurationsdateien oder Logfiles während der Laufzeit editiert und sofort sichtbar werden, z. B. wenn Quellcode oder Konfigurationsdateien auf dem Host bearbeitet und sofort im Container sichtbar werden sollen.
- Im Beispiel wird ein lokales Verzeichnis des Hosts (/home/student/myproject) mit einem Verzeichnis im Container (/app/myproject) verknüpft, über den Befehl `docker container run -v /home/student/myproject:/app/myproject`
- Die Option -v steht für volume und definiert hier ein Bind Mount, bestehend aus zwei Pfadangaben:
  - Host-Pfad: /home/student/myproject → verweist auf das lokale Verzeichnis auf dem Hostsystem.
  - Container-Pfad: /app/myproject → definiert den Mount-Punkt im Container.

Quelle: cloud-computing/origin/WDS125 - Cloud Computing (SCA)/05 Docker/3-Docker/3-Docker.pdf, Seiten 44–49

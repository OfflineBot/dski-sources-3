# Probe-Programmentwurf

# Ausgangsprojekt: Begrüßungsservice

```text
Programmentwurf/
  compose.yaml          # leer, von Studierenden auszufüllen
  spring/               # Gradle-Projekt, Env-Datei und selbst erstelltes Dockerfile
  nginx/default.conf    # bereitgestellte Proxy-Konfiguration
```

Voraussetzungen: Java 21, Docker mit Linux-Containern und Docker Compose v2.
Alle Aufgabenbefehle werden aus `Programmentwurf` ausgeführt.

```sh
./spring/gradlew -p spring bootJar
```

Unter Windows: `spring\gradlew.bat -p spring bootJar`.
Die JAR-Datei entsteht unter `spring/build/libs/app.jar`.
Das Dockerfile ist unter `spring/Dockerfile` selbst zu erstellen;
sein Build-Kontext ist `spring`, sodass COPY weiterhin `build/libs/app.jar` verwendet.
Die Datei `spring/greeting.env` enthält die Ausgangskonfiguration.

Endpunkt: `GET /?name=Anna`, Container-Port 8080.
Sollverhalten: `dev` begrüßt jeden Namen; `prod` akzeptiert nur die konfigurierte Gästeliste
und antwortet andernfalls mit HTTP 403. Das Ausgangsprojekt enthält bewusst Fehler.

Nginx verwendet zunächst den Host-Port 8081; bei der Netzwerk- und Compose-Aufgabe
passen die Studierenden die Zieladresse selbst an.
Die Aufgaben stehen im benachbarten Ordner `Aufgabenstellung`.

## Dateien in diesem Ordner

| Datei | Zweck |
| --- | --- |
| `TASKS.md` | diese Aufgabenstellung |
| `Programmentwurf.zip` | Startprojekt aus `origin/` (`compose.yaml`, `nginx/default.conf`, `spring/` mit Gradle-Projekt und `greeting.env`) |

## Hinweis zur Zuordnung

Der im Text genannte Ordner `Aufgabenstellung` ist in `origin/` nicht vorhanden.

Quelle: cloud-computing/origin/WDS125 - Cloud Computing (SCA)/06 Probe-Programmentwurf/Programmentwurf/Programmentwurf.zip, Datei Programmentwurf/README.md

# Grundlagen

## Paradigma

- Manueller Aufwand: Hafenarbeiter betreten Schiff und entladen die Fracht.
- Gefahr: Kein sicheres Arbeitsumfeld.
- Performance: Hafenbrücken werden zum Flaschenhals.
- Unsichere Dauer: Keine Planung da abhängig von Verfügbarkeit der Arbeiter.

- Standardisierung: 90% aller Frachtcontainer sind Standardcontainer.
- Sicherheit: Massive Reduktion der Frachtschäden und Diebstähle.
- Performance: Sehr kurze Dauer für Ladung und Endladung, durch Infrastruktur.
- Planung: Standardisierte Intrastruktur gibt Planungssicherheit für Dauer und Kosten.

### Notizen

- Das Grundparadigma von Docker ist der Standardcontainer in der Frachtschifffahrt.
- Vor der Einführung der Standardcontainer: sehr hoher manueller Aufwand für die Ladung und die Entladung von Schiffen, da die Arbeiter das Schiff betreten und die Fracht händisch aufnehmen mussten. Dies resultierte in Transportschäden und gefährdete zum Teil die Sicherheit der Arbeiter, da die Hafenbrücken oft zum Flaschenhals wurden.
- Unklare Planungsgrundlage durch die unklare Verfügbarkeit von Arbeitern am Hafen, die Behinderungen beim Entladen und die Verfügbarkeit von Lagerplatz. Frachtschäden und Frachtdiebstähle waren keine Seltenheit.
- Die Einführung der Standardcontainer löste einen regelrechten Paradigmenwechsel aus, der die Frachtschifffahrt massiv veränderte. Heute sind ca. 90% aller Frachtcontainer Standardcontainer, deshalb ist die gesamte Infrastruktur an den Häfen und den Schiffen auf sie optimiert.
- Vergleich der ersten Jahre: Vor Einführung der Standardcontainer benötigte eine 18-köpfige Crew eine 8 Stunden Schicht um 80 Tonnen zu entladen. Nach der Einführung konnte eine 9-köpfige Crew in der gleichen Zeit 2000 Tonnen entladen.

## Was ist Docker

- Docker ist ein Werkzeug mit dem Anwendungen gebaut, verteilt und betrieben werden können.
- Es ist der de-facto Standard zur Prozessvirtualisierung unter Nutzung der Kernelfunktionen cgroups und namespaces.
- Docker ist kostenlos und der Code der Ausführungsumgebung, sowie dem Speicherformat wurden teilweise offengelegt, wodurch die Technologie große Verbreitung fand.
- Ähnlich zum Container in der Schifffahrt legte Docker den Grundstein für weitere Werkzeuge und Umsetzungen des Cloud Computing.
- Docker besteht aus einem Client der Befehle absetzt und einem Deamon (Server), der die Befehle entgegennimmt und ausführt.

### Notizen

- Docker ist egal welche Programmiersprache verwendet wird: Es wird ein standardisiertes und portables Abbild (Image) der Anwendung und der notwendigen Systemkonfiguration erzeugt, das der Empfänger nach Erhalt direkt ausführen kann.
- Um diesen einfachen Workflow umzusetzen, nutzt Docker die Prozessvirtualisierung, die auf den Linux-Kernfunktionen cgroups und namespaces basiert.
- Massive Popularität aufgrund der intuitiven Handhabung und der freien Nutzung.
- Docker hat den Grundstein für eine nachhaltige Veränderungen des Anwendungsbetriebs gelegt und so das Entstehen weiterer Werkezuge für den optimierten Betrieb von Cloud Computing ermöglicht.
- Docker-Client: ein Kommandozeilen-Programm, das die eigegebenen Befehle übersetzt und via einer Rest-Schnittstelle an den Docker-Deamon überträgt.
- Docker-Deamon: verantwortlich für die Erstellung und Parametrisierung der Linux-Container; nimmt die Überführung der portablen Abbilder in ausführbare Einheiten vor.

## Docker — Überblick

![Docker — Überblick](images/docker-overview.png)

### Notizen

- Das Schaubild gibt einen grundlegenden Überblick über die wichtigen Grundpfeiler von Docker.
- Docker Image: zentral bei der Verwendung von Docker. Eine Beschreibung der Laufzeitumgebung samt aller notwendigen Konfigurationen; selbst nicht ausführbar.
- Docker Container: eine Laufzeitrepräsentation eines Docker Images.
- Docker Registry: Darüber werden Docker Images verteilt, das heißt Images können dort abgelegt und bezogen werden.
- Dockerfile: Darüber können Docker Images selbst erstellt werden.
- Hilfe zur Verinnerlichung dieses Workflows: sich ein Docker Image als ein Kuchenrezept vorstellen.
  - Anhand des Rezepts lassen sich ein oder mehrere Kuchen dieser Art parallel oder nacheinander erstellen.
  - Das Rezept kann über eine Internetplattform (vgl. Docker Registry) verteilt und bezogen werden.
  - Das Rezept lässt sich in eigener kreativer Arbeit verfassen (vgl. Dockerfile).

Quelle: cloud-computing/origin/WDS125 - Cloud Computing (SCA)/05 Docker/3-Docker/3-Docker.pdf, Seiten 3–5

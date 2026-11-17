# Aktivitätsdiagramme und BPMN

![Folie 2](images/folie-02.png)

## So werden wir vorgehen - Das RE-Vorgehensmodell

![So werden wir vorgehen - Das RE-Vorgehensmodell](images/folie-03.png)

## Nachteil der Use Case-Schablone

Die Use Case-Schablone suggeriert eine Sequenz der Abarbeitung, die u.U. gar nicht gegeben ist:

Beispiel (UC #002 Kundenauftrag ausführen)

![Nachteil der Use Case-Schablone](images/folie-04.png)

Aktivität 4 und 5 müssen nicht sequentiell ablaufen

Dieser Nachteil kann durch Aktivitätsdiagramme beseitigt werden.

## Das Aktivitätsdiagramm zu UC #002

![Das Aktivitätsdiagramm zu UC #002](images/folie-05.png)

## Grundlegende Notationssymbole eines AD

![Grundlegende Notationssymbole eines AD](images/folie-06.png)

- Aktivität — Aktivitätsschritt aus dem UC
- Entscheidungsknoten
- Synchronisationsbalken
- Startknoten
- Endeknoten
- [Bedingung] — Kontrollfluss mit Bedingungsangabe

## Modellierung wichtiger logischer Operatoren

![Modellierung wichtiger logischer Operatoren](images/folie-07.png)

- Aufteilendes UND — Parallelisierungsknoten
- Zusammenführendes UND — Synchronisationsknoten
- Aufteilendes XOR — Entscheidungsknoten
- Zusammenführendes XOR — Zusammenführungsknoten

## Weiterführende Elemente

![Weiterführende Elemente](images/folie-08.png)

## Exkurs: Gedanklicher Zusammenhang von SA und AD

![Exkurs: Gedanklicher Zusammenhang von SA und AD](images/folie-09.png)

NB:
`<<datastore>>` kann man auch weglassen.
Es kennzeichnet lediglich die persistente Speicherung.

## Exkurs: BPMN 2.0 – die elegantere Lösung, aber halt nicht UML…

![Exkurs: BPMN 2.0 – die elegantere Lösung, aber halt nicht UML…](images/folie-10.png)

## BPMN 2.0 – Die wichtigsten Notationssymbole

![BPMN 2.0 – Die wichtigsten Notationssymbole](images/folie-11.png)

- Aufgabe
- Teilaufgabe
- Startereignis
- Endereignis
- Zeitliches Ereignis
- Kontrollfluss
- Standardverzweigung
- Gerichtete (Daten-)Assoziation
- ungerichtete Assoziation
- Anmerkungen
- Datenobjekt
- Datenspeicher
- Pool und Lane
- Gateways:
  - Exklusives ODER
  - Logisches ODER
  - Logisches UND

Quelle: systems-engineering/origin/WDS125 - Systems Engineering (BäM)/11 LE 8_ Aktivitätsdiagramme, BPMN - Modellierung der alternativen Ablaufszenarien/Folien der Lerneinheit/10.RE-AD-BPMN.pdf, Seiten 1–11

# Namensregeln

Ereignisse werden im Kontext des Systems gesucht.

Externer Ereignisname = Name des Nachbarsystems + Grund für den Datenfluss.

- Kunde gibt Kauforder.

Zeitlicher Ereignisname = Zeit für + auszuführende Tätigkeit.

- Zeit für Börsenschluss (soll heißen: Bei Ende Börsenhandel noch offene Kaufordern löschen).
- Zeit für das Löschen abgelaufener Order

## Ereignisliste – dient der Sammlung aller relevanten Ereignisse, für die das System einen Dienst ausführen können muss

| Ereignisname | Zugehörige Datenflüsse |
| --- | --- |
| Kunde gibt Kauforder | Kauforder (I)<br>Auftragsbestätigung (O)<br>Ungültige Order (O) |
| Zeit für Börsenschluss | Gelöschte Order (O) |
| ... | ... |

I – Input des Systems (eingehender Datenfluss); O – Output des Systems (ausgehender Datenfluss)

## Zusammenhang zwischen Ereignisliste und ERM

> Merke:
> Zu jedem nicht-trivialen Ereignis aus der Ereignisreaktionsliste wird ein eigenes Ereignisreaktionsmodell erstellt!

Quelle: systems-engineering/origin/WDS125 - Systems Engineering (BäM)/08 LE 5_ Essenzielle Modellierung - Paradigma der ereignisorientierten Zerlegung/Folien der Lerneinheit/06.RE-ERM.pdf, Folien 12–14

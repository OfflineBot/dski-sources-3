# Erkennen von zeitlichen Ereignissen

Zeitliche Ereignisse werden durch das Eintreten eines vorgegebenen Zeitpunktes ausgelöst.

Das Ereignis endet, wenn es einen oder mehrere Datenflüsse nach Außen abgegeben hat.

Beispiel:

- Die Kauforder konnte nicht am gleichen Börsentag platziert werden.
- Zeitliches Ereignis: Ende des Börsentages.
- Reaktion: Order löschen, Kunden informieren.

## Zeitliches Ereignis - Zeit für Börsenschluss

![Zeitliches Ereignis - Zeit für Börsenschluss](images/folie-10.png)

## Denken Sie daran – Essenz, Essenz, Essenz!! Wir sind immer noch in der Problemdomäne und wollen das wahre Problem verstehen (nicht die IT-Probleme)

Die essentielle Sicht zeigt das System als eine Menge von implementierungsunabhängigen Anforderungen.

Beispiel:

- Im Ereignis Kunde gibt Kauforder wird die Order zuerst geprüft und anschließend registriert.
    - Funktionen: prüfe Order, registriere Order.
    - Daten: Kundendaten, Orderdaten.
    - Die Daten werden anschließend von anderen Ereignissen benötigt. Bsp.: Zeit für Börsenschluss.
- Wie das Ereignis technisch funktioniert ist uninteressant (nicht essentiell).

Quelle: systems-engineering/origin/WDS125 - Systems Engineering (BäM)/08 LE 5_ Essenzielle Modellierung - Paradigma der ereignisorientierten Zerlegung/Folien der Lerneinheit/06.RE-ERM.pdf, Folien 9–11

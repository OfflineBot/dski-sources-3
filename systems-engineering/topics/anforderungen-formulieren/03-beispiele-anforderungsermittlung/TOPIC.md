# Beispiel: Product Use Case #001

1. **Use Case**: #001 Neukunde erfassen.
2. **Ziel**: Ein neuer Kunde wurde erfasst.
3. **Vorbedingung**: es handelt sich um eine natürliche Person (Endkunde) und die Kundenstammdaten liegen vor.
4. **Nachbedingung Erfolg**: Die für Auftragsdurchführung und Kundenkommunikation notwendigen Stammdaten des neuen Kunden wurden erfasst und gespeichert.
5. **Nachbedingung Fehlschlag**: Der Kundenstammdatensatz wurde nicht im CRM-System angelegt. Die Gründe für den Fehlschlag wurden mitgeteilt.
6. **Akteur**: Kundensachbearbeiter.
7. **Auslösendes Ereignis**: Ein Kaufauftrag wurde durch einen Neukunden erteilt.
8. **Beschreibung**:
   1. Der Kundensachbearbeiter validiert die Kundenstammdaten (Vorname, Nachname, Lieferadresse, Rechnungsadresse, Geburtsdatum) auf Plausibilität und Vollständigkeit.
   2. Der Kundensachbearbeiter legt den neuen Kundenstammsatz im CRM-System an.
   3. Das CRM-System generiert die Kundennummer und speichert sie im Kundenstammsatz.

   **Alternativen**:

   1a. Die Validierung war nicht erfolgreich: Unter Angabe der Gründe für den Fehlschlag bricht der Kundensachbearbeiter den UC ab.

## Ermittlung der Anforderungen aus Aktivität 1

FANF#001: Das System muss dem Kundensachbearbeiter die Möglichkeit bieten, die Kundenstammdaten eines Neukunden einzugeben.

FANF#002: Das System muss die Kundenstammdaten des Neukunden auf Plausibilität überprüfen. Plausibilitätskriterien: ET#001.

FANF#003: Wenn mindestens 1 Plausibilitätskriterium aus FANF#002 nicht erfüllt ist, muss das System den Kundensachbearbeiter zur Korrektur auffordern und die Speicherung des Kundenstammdatensatzes verweigern.

## Beispiel Typ 1 – Selbständige Systemaktivität

FANF #004: Wenn die Plausibilitätsprüfung nach FANF#002 erfolgreich war, muss das System den Kundenstammdatensatz des Neukunden in der Datenbank "CRM-DB" speichern.

## Beispiel Typ 1

FANF#005: Wenn ein Neukunde nach FANF#004 erfolgreich angelegt wurde, muss das System eine Kundennummer für den Neukunden generieren. Regel: Letzte Kundennummer + 1.

FANF #006: Sobald die Kundennummer (FANF#005) erfolgreich erzeugt wurde, speichert das System die Kundennummer im Stammdatensatz des Neukunden (vgl. Data Dictionary) in der Datenbank "CRM-DB" ab.

## Beispiel Typ 3 - Schnittstellenanforderung

NFANF#099: Solange das System online ist, muss es in der Lage sein, Softwareupdates von einem zentralen Administrationsrechner über das LAN zu empfangen und einzuspielen.

## Übung

Welcher Typ liegt hier jeweils vor?

1. Der Kunde will, dass das System Deutsch, Englisch und Chinesisch als Benutzersprache unterstützt.
2. Der Kunde möchte, dass das System auch beliebige Sprachen in der Zukunft unterstützen kann.
3. Das System muss nicht mandantenfähig sein, soll diese Fähigkeit aber zukünftig nicht unmöglich machen.

Quelle: systems-engineering/origin/WDS125 - Systems Engineering (BäM)/13 LE 10_ Anforderungen formulieren - Anforderungen an gute Anforderungssätze/Folien der Lerneinheit/12.RE-Anforderungen.pdf, Folien 8–13

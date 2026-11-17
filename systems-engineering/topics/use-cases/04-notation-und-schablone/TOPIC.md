# Notationsformen für Use Cases

- Bei einfachen Use Cases reicht eine umgangssprachliche Beschreibung aus.
- Bei komplexen Use Cases kann eine Use Case-Schablone (use case template) verwendet werden.

## Use Case-Schablone

1. **Use Case**: Name, bestehend aus zwei oder drei Wörtern (was wird getan?)
2. **Ziel**: globale Zielsetzung bei erfolgreicher Ausführung des Use Case
3. **Vorbedingung**: Erwarteter Zustand, vor Beginn
4. **Nachbedingung Erfolg**: Erwarteter Zustand nach erfolgreicher Ausführung, d.h. Ergebnis des Geschäftsprozesses
5. **Nachbedingung Fehlschlag**: Erwarteter Zustand, wenn das Ziel nicht erreicht werden kann
6. **Akteure**: Rollen von Personen oder andere Systeme, die den Use Case auslösen oder daran beteiligt sind
7. **Auslösendes Ereignis**: Wenn dieses Ereignis eintritt, dann wird der Use Case initiiert
8. **Beschreibung**:
   - 1 Erste Aktion
   - 2 Zweite Aktion

   **Erweiterungen**:
   - 1a Erweiterung des Funktionsumfangs der erste Aktion

   **Alternativen**:
   - 1a Alternative Ausführung der ersten Aktion
   - 1b Weitere Alternative zur ersten Aktion

## Beispiel für die umgangssprachliche Formulierung: Use Case: Kundenauftrag ausführen

> Use Case: Kundenauftrag ausführen
>
> Eine Kundenbestellung kommt in der Versandabteilung an. Neukunden werden im System registriert und der Versand an diese Kunden erfolgt ausschließlich per Nachnahme oder per Bankeinzug. Für alle lieferbaren Artikel wird die Rechnung erstellt und als Auftrag an das Lager weitergegeben. Sind einige der gewünschten Artikel nicht lieferbar, so wird der Kunde informiert und die Nachlieferung im System vorgemerkt. Alle erstellten Rechnungen werden an die Buchhaltung weitergegeben.
>
> An diesem Use Case sind folgende Akteure beteiligt: Kundensachbearbeiter, Lagersachbearbeiter und Buchhaltung.

## Gleiches Beispiel mit UC-Schablone

- **Use Case**: #002 Kundenauftrag ausführen
- **Ziel**: Ware an Kunden geliefert
- **Vorbedingung**: -
- **Nachbedingung Erfolg**: Ware ausgeliefert (auch Teillieferungen), Rechnungskopie bei Buchhaltung
- **Nachbedingung Fehlschlag**: Kunde wurde mitgeteilt dass nichts lieferbar ist
- **Akteure**: Kundensachbearbeiter, Lagersachbearbeiter, Buchhaltung
- **Auslösendes Ereignis**: Bestellung des Kunden liegt vor

**Beschreibung**:

- 1 Die Kundendaten werden auf Aktualität geprüft
- 2 Lieferbarkeit prüfen
- 3 Rechnung erstellen: UC #020 Rechnung erstellen
- 4 Auftrag vom Lager ausführen lassen
- 5 Rechnungskopie an Buchhaltung geben

**Erweiterung**:

- 1a Wenn die gespeicherten Kundendaten nicht aktuell sind: UC #004 Kundendaten aktualisieren
- 2a Für nachlieferbare Artikel: UC #003 Nachlieferung veranlassen

**Alternativen**:

- 1a Wenn der Besteller noch nicht Kunde ist: UC #001 Neukunde erfassen
- 3a Wenn ein Artikel nicht lieferbar: Kunde mitteilen, dass nicht geliefert werden kann. UC beenden.

Quelle: systems-engineering/origin/WDS125 - Systems Engineering (BäM)/10 LE 7_ Use Cases - Modellierung der Anwendungsfälle/Folien der Lerneinheit/09.RE-UC.pdf, Folien 11–14

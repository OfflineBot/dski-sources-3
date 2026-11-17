# Systemanalyse – WWIDS120 – 22. September 2021

Studiengang: Wirtschaftsinformatik – Data Science
Modul: W3WI_101.2
Klausurteil: Systemanalyse – 2. Semester
Kurse: WWIDS120
Datum: 22. September 2021
Dauer: 70 Minuten
Max. Punkte: 60
Anzahl der Seiten: 8 (ohne diese Seite. Bitte überprüfen!)
Hilfsmittel: keine Hilfsmittel
Hinweis: Antworten nur auf diesen Klausurblättern!

Wichtige Hinweise

- Schreiben Sie Ihre Antworten nur auf die Klausurblätter. Sollte der Platz nicht ausreichen, schreiben Sie auf der Rückseite weiter. Antworten auf anderen Blättern werden nicht gewertet!
- Die Klausur ist geheftet abzugeben!

Viel Erfolg!

| Aufgabe Nr.: | 1 | 2 | 3 | 4 | ∑ |
|---|---|---|---|---|---|
| max. Punktzahl: | 20 | 10 | 10 | 20 | 60 |

## 1. Bitte beantworten Sie die nachfolgenden Fragen.

**(a) [4 Punkte]** Erläutern Sie das Systemverständnis in einem Geschäftsprozessmodell und in einem Product Use Case.

**(b) [3 Punkte]** Nennen und erläutern Sie den Grund, warum FISCUS beim zweiten Anlauf scheiterte.

**(c) [3 Punkte]** Nennen und erläutern Sie die Arten von Akteuren eines Product Use Cases.

**(d) [10 Punkte]** Nennen und erläutern Sie die Komponenten von Scrum.

## 2. Bei den folgenden Fragen handelt es sich um Single-Choice-Fragen.

Kreuzen Sie die korrekte Antwort mit X an!
Es ist immer nur eine der angegebenen Antworten korrekt!
Eine falsche Antwort führt jeweils zu 1 Punkt Abzug!

**(a) [1 Punkt]** Ein Use-Case-Diagramm ist...

- A. eine grafische Darstellung eines Product Use Case des zu modellierenden Systems
- B. eine grafische Zusammenfassung aller Product Use Cases und Akteure des zu modellierenden Systems
- C. nichts davon. Die Aussagen a. und b. sind beide falsch

**(b) [1 Punkt]** Was bedeutet die Regel „Who has the ball“?

- A. Immer aus Sicht des Akteurs schreiben
- B. Immer angeben, wer die Aktivität ausführt
- C. Immer angeben, für wen etwas getan wird

**(c) [1 Punkt]** Was meint der „Coffee-Break-Test“?

- A. Den sinnvollen Umfang einer Aktivität
- B. Den sinnvollen Umfang eines Product Use Cases
- C. Nichts davon. Die Aussagen a. und b. sind beide falsch

**(d) [1 Punkt]** Welche Aussage zum auslösenden Datenfluss einer Ereignisreaktion ist falsch?

- A. Das Nachbarsystem, das ein Ereignis auslöst, muss auch immer dasjenige sein, das die Reaktion erhält
- B. Jedes auslösende externe Ereignis erzeugt einen eindeutigen Datenfluss in das System
- C. Datenspeicher sind immer systemintern und stellen keine Nachbarsysteme dar

**(e) [1 Punkt]** Was ist keine Aufgabe des Scrum Masters?

- A. Die fachliche Leitung des Teams
- B. Die fachliche Unterstützung des Teams
- C. Die fachliche Moderation des Teams

**(f) [1 Punkt]** Stimmt diese Aussage: „Für die Essenzbildung müssen Ablaufreihenfolgen und Abhängigkeiten in den Tätigkeiten der Problemdomäne betrachtet werden, die keinen fachlichen Hintergrund haben.“

- A. Die Aussage ist richtig
- B. Die Aussage ist falsch

**(g) [1 Punkt]** Was ist die korrekte Definition eines Lastenhefts?

- A. Im Lastenheft wird definiert WAS und WOFÜR zu lösen ist
- B. Im Lastenheft wird definiert WAS WIE zu lösen ist

**(h) [1 Punkt]** Was ist keine Ereignisart, die in der Systemanalyse betrachtet wird?

- A. Echte Ereignisse
- B. Externe Ereignisse

**(i) [1 Punkt]** Welche Aussage stimmt bezüglich Alternativen in einem Product Use Case?

- A. Eine Alternative ergänzt eine Aktivität im Product Use Case
- B. Zu einer Alternative kann es keine Erweiterungen geben
- C. Nichts davon. Die Aussagen a. und b. sind beide falsch

**(j) [1 Punkt]** Welche Aussage zu den Beziehungsarten eines Product Use Cases ist richtig?

- A. „include“ erweitert einen Use Case unter bestimmten Bedingungen
- B. „extend“ wird für Erweiterungen und Alternativen eines Use Cases benutzt
- C. Nichts davon. Die Aussagen a. und b. sind beide falsch

## 3. [10 Punkte]

Modellieren Sie eine konsolidierte Entscheidungstabelle für folgende Besuchsregelung eines Krankenhauses:

Die Patientin kann ohne Einschränkungen innerhalb der Besuchszeit besucht werden, sofern keine ansteckende Krankheit bei ihr vorliegt und sie kein Fieber hat. Außerhalb der Besuchszeit ist grundsätzlich eine Krankenschwester als Begleitung erforderlich. Falls die Patientin eine ansteckende Krankheit hat, werden Besuche ganz abgelehnt. Wenn die Krankheit nicht ansteckend ist, die Patientin aber Fieber hat, darf der Besuch innerhalb der Besuchszeit maximal 30 Minuten betragen. Außerhalb der Besuchszeiten dürfen Patienten mit Fieber nicht besucht werden.

Konsolidierte Entscheidungstabelle:

## 4.

Die All-for-You AG ist ein IT-Dienstleister, der das Outsourcing von ERP-Systemen als Software-as-a-Service großen Unternehmenskunden anbietet. Für den Support der Unternehmenskunden wird ein neues Ticketsystem eingeführt. Sie sollen dafür die Systemanalyse übernehmen und die Product Use Cases modellieren.

In einem Gespräch mit der All-for-You AG zum **PUC #001 Ticket im First-Level-Support bearbeiten** haben Sie folgende Informationen für diesen Use Case erhalten:

„Damit ein Mitarbeiter ein Ticket im First-Level-Support bearbeiten kann, muss durch den Kunden im Ticketsystem ein Ticket mit niedriger Priorität angelegt und anschließend automatisch durch das Ticketsystem einem Mitarbeiter zugewiesen worden sein.

Ist das passiert, sieht die Ticketbearbeitung wie folgt aus: Der Mitarbeiter schaut sich das Ticket im Ticketsystem erst einmal an und informiert sich über das vom Kunden beschriebene Problem. Dann sucht der Mitarbeiter nach gleichen/ähnlichen Problemen in der Wissensdatenbank der All-for-You AG. Wenn keine Lösung in der Wissensdatenbank dokumentiert ist, dann schiebt der Mitarbeiter das Ticket zum Second-Level-Support weiter. Damit wäre dann der Fall für ihn erledigt. Hat er aber Erfolg und findet in der Wissensdatenbank einen Lösungsvorschlag, dann nimmt er Kontakt mit dem Kunden auf, um ihm den Lösungsvorschlag mitzuteilen. Der Kunde testet den Lösungsvorschlag und wenn alles klappt, schließt der Mitarbeiter das Ticket. Sollte das Problem beim Kunden mit dem Lösungsvorschlag nicht gelöst werden können, dann schiebt der Mitarbeiter das Ticket zum Second-Level-Support.“

Erstellen Sie dazu bitte

**(a) [15 Punkte]** den Product Use Case „PUC #001 Ticket im First-Level-Support bearbeiten“

**(b) [5 Punkte]** und erstellen Sie das zugehörige Aktivitätsdiagramm.

Platz für Ihre Lösungen haben Sie auf den nächsten Seiten!
Lösungen auf dieser Seite werden nicht gewertet!

Quelle: systems-engineering/origin/WDS125 - Systems Engineering (BäM)/15 Alte Klausuren/WWIDS120.Klausurteil_SA/WWIDS120.Klausurteil.SA.pdf

# Klausur Systemanalyse – WWIDS119 – 18. Juni 2020

Studiengang: Wirtschaftsinformatik – Data Science
Modul: W3WI_101
Klausurteil: Systemanalyse/2. Semester
Kurse: WWIDS119
Datum: 18. Juni 2020
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

**(a) [2 Punkte]** Erläutern Sie, was man unter „Essenz“ versteht.

**(b) [2 Punkte]** Erläutern Sie den Zweck eines Ereignisreaktionsmodells.

**(c) [3 Punkte]** Erläutern Sie analytische und konstruktive Qualitätssicherung bei Scrum.

**(d) [4 Punkte]** Erläutern Sie das klassische V-Modell.

**(e) [2 Punkte]** Erläutern Sie den Unterschied zwischen evolutionärem und inkrementellem Prozessmodell.

**(f) [3 Punkte]** Erläutern Sie die drei Arten von Prototypen, die es neben der Unterscheidung in vertikale und horizontale Prototypen gibt.

**(g) [2 Punkte]** Nennen Sie die Aufgaben eines Lastenhefts.

**(h) [2 Punkte]** Nennen Sie vier Bedingungen, unter denen die Agile Softwareentwicklung ungeeignet ist.

## 2. Bei den folgenden Fragen handelt es sich um Single-Choice-Fragen.

Kreuzen Sie die korrekte Antwort mit X an!
Es ist immer nur eine der angegebenen Antworten korrekt!
Eine falsche Antwort führt jeweils zu 1 Punkt Abzug!

**(a) [1 Punkt]** Welche Aussage ist richtig?

- A. Ein Nachbarsystem ist immer auch ein Akteur
- B. Ein Akteur ist immer auch ein Nachbarsystem
- C. Akteur und Nachbarsystem können identisch sein

**(b) [1 Punkt]** Welche Aussage ist falsch?

- A. Nach „prüfen“, „validieren“ etc. kommt immer genau eine Alternative
- B. „extend“ wird für Erweiterungen und Alternativen eines Use Cases benutzt

**(c) [1 Punkt]** Was war kein Grund dafür, dass FISCUS scheiterte?

- A. Personalmangel
- B. Überforderung der Objektorientierung
- C. Projektmanagementfehler

**(d) [1 Punkt]** Welche Rolle spielt das Projektmanagement bei Scrum?

- A. gar keine
- B. hilft dem Team
- C. führt die Gespräche mit dem Product Owner

**(e) [1 Punkt]** Was ist kein Punkt des Agilen Manifests?

- A. „Individuals and interactions over processes and tools“
- B. „Team skills over financial incentives“
- C. „Customer collaboration over contract negotiation“

**(f) [1 Punkt]** Was ist keine Ereignisart in der Systemanalyse?

- A. Personelle Ereignisse
- B. Zeitliche Ereignisse
- C. Externe Ereignisse

**(g) [1 Punkt]** Wie kann eine Entscheidungstabelle in einen Use Case integriert werden?

- A. Auf sie wird in der entsprechenden Aktivität verwiesen
- B. Sie wird als Tabelle im Erweiterungsteil eingefügt
- C. Gar nicht

**(h) [1 Punkt]** Eine Extend-Beziehung in einem Use-Case-Diagramm ist nur möglich für. . .

- A. den Erweiterungsteil eines Use-Cases
- B. den Alternativenteil eines Use-Cases
- C. den Erweiterungs- und den Alternativenteil

**(i) [1 Punkt]** Der Coffee-Break-Test ist eine Daumenregel für. . .

- A. den angemessenen Umfang eines Product Use Cases
- B. den angemessenen Umfang einer Aktivität in einem Product Use Case
- C. die angemessene Anzahl von Product Use Cases

**(j) [1 Punkt]** Ereignisreaktionsmodelle modelliert man

- A. immer
- B. nur bei Bedarf

## 3. [10 Punkte]

Modellieren Sie eine konsolidierte Entscheidungstabelle für folgenden Sachverhalt:

Muss in der Buchhandlung „BäMs Lesefreuden“ für einen Kunden ein Buch bestellt werden, weil es nicht vorrätig ist, wird zunächst geprüft, ob das Buch lieferbar ist. Für nicht-lieferbare Bücher wird die Bestellung abgelehnt. Bei lieferbaren Büchern wird die Bonität des Kunden geprüft. Wenn diese nicht in Ordnung ist, kann nur auf Vorauskasse bestellt werden. Ist die Bonität in Ordnung wird immer auf Rechnung bestellt und der Kunde zahlt erst nach Erhalt des Buchs.

Konsolidierte Entscheidungstabelle:

## 4.

Für ein Fitnessstudio wird ein neues Mitgliederverwaltungssystem entwickelt. Eine Funktion des Mitgliederverwaltungssystems soll die Registrierung neuer Mitglieder durch einen Mitarbeiter des Fitnessstudios ermöglichen. Bei der Anforderungserhebung haben Sie dazu folgende Informationen erhalten:

„Kommt jemand zu uns neu in das Fitnessstudio, dann müssen wir diese Person zuerst im System als neues Mitglied registrieren. Dazu gibt der Mitarbeiter die Registrierungsdaten des neuen Mitgliedes in das Mitgliederverwaltungssystem ein. Das System prüft dann die Daten auf formale Plausibilität, also ob alle erforderlichen Angaben gemacht wurden. Danach klärt der Mitarbeiter mit dem neuen Mitglied, ob er Basis- oder Premiummitglied werden will und wählt den entsprechenden Mitgliedsvertrag im System aus. Dieser Vertrag wird zweimal ausgedruckt und vom Kunden unterschrieben. Eine Kopie bekommt das neue Mitglied, eine bekommen wir. Dies wird im System vermerkt, damit wir wissen, dass der Vertrag vom Mitglied unterschrieben und eine Version ihm auch ausgehändigt wurde. Unterschreibt die Person nicht, weil sie mit dem Vertrag nicht einverstanden ist, dann wird die Registrierung abgebrochen. Ansonsten beschreibt das Mitgliederverwaltungssystem die Mitgliedskarte des neuen Mitglieds mit dessen Daten und der Mitarbeiter händigt diese Karte dem Mitglied aus.“

Erstellen Sie dazu bitte

**(a) [15 Punkte]** den Product Use Case „PUC 001 Neues Mitglied registrieren“

**(b) [5 Punkte]** und erstellen Sie das zugehörige Aktivitätsdiagramm.

Platz für Ihre Lösungen haben Sie auf den nächsten Seiten!
Lösungen auf dieser Seite werden nicht gewertet!

Quelle: systems-engineering/origin/WDS125 - Systems Engineering (BäM)/15 Alte Klausuren/WWIDS19.Klausurteil_SA/WWIDS19.Klausur.SA.pdf

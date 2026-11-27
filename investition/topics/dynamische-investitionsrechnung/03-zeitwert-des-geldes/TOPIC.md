# Zeitwert des Geldes: Endwert und Barwert

## Zeitstrahl

Bei langfristigen Projekten fallen Ein- und Auszahlungen in der Regel zu unterschiedlichen Zeitpunkten an. Ein erstes Instrument, um diese Zahlungsflüsse visuell darzustellen, ist der **Zeitstrahl**. Der Zeitstrahl zeigt eine Reihe von Cash-Flows über mehrere Zeiträume hinweg.

Der Zeitpunkt t0 stellt den aktuellen Zeitpunkt (heute) dar. Der Zeitpunkt t1 liegt eine Periode (i.d.R. 1 Jahr) in der Zukunft, t2 dementsprechend 2 Perioden. Der Abstand zwischen den Zeitpunkten stellt den Zeitraum dar, in diesem Fall 1 Jahr Abstand. (Beispiel auf der Folie: t0 = −10, t1 = +6, t2 = +6)

## Die drei Regeln

**Regel 1: Nur Zahlungen zum gleichen Zeitpunkt können verglichen oder zusammengelegt werden**

Bei Vergleichen von langfristigen Projekten sollten die Projekte mit dem höchsten Gesamt-Zahlungszufluss gewählt werden. Ein Euro heute und ein Euro in einem Jahr sind nicht gleichwertig. Heute Geld zu besitzen ist wertvoller, da dieses einen Zinsertrag erwirtschaften kann. Um daher Zahlungen vergleichen zu können, müssen sie auf den gleichen Zeitpunkt „verschoben" werden.

**Regel 2: Zahlungen in die Zukunft verschieben (Aufzinsung)**

Um eine Zahlung um ein Jahr in die Zukunft zu verschieben, wird die Annahme getroffen, dass wir das Geld für ein Jahr anlegen und einen Zinssatz i erhalten können.

Beispiel: Sie haben heute 1.000 € und wollen es in die Zukunft verschieben. Der Zinssatz ist 10%. Wieviel Geld haben Sie in 2 Jahren?

t0 = 1.000 → (× 1,1) → t1 = 1.100 → (× 1,1) → t2 = 1.210

Der Wertunterschied zwischen heutigem Geld und zukünftigem Geld stellt den Zeitwert des Geldes dar. In diesem Fall ist er 210 € über 2 Jahre. Zu beachten ist, dass die Zinsen auf den ursprünglichen Betrag 2 × 100 = 200 € betragen, während die Zinsen auf die Zinsen (**Zinseszinsen**) 10% × 100 = 10 € betragen. Daraus ergibt sich die Endwertregel.

**Regel 3: Zahlungen in die Vergangenheit verschieben (Diskontierung / Abzinsung)**

Um eine Zahlung um ein Jahr in die Vergangenheit zu verschieben, wird die Annahme getroffen, dass wir die vorherigen Zinsen in der Vergangenheit quasi noch nicht erhalten haben. Wir müssen sie also vom aktuellen Wert abziehen.

Beispiel: Sie erwarten in 2 Jahren eine Zahlung von 1.000 €. Der Zinssatz sei 10%. Wie hoch ist der Wert dieser Zahlung heute?

t2 = 1.000 → (: 1,1) → t1 = 909,09 → (: 1,1) → t0 = 826,45

Alle abgezinsten Zahlungen sind gleichwertig. 1.000 € in 2 Jahren entspricht 909,09 € in 1 Jahr und 826,45 € heute. Genau wie umgekehrt gilt, dass 826,45 € heute 909,09 € in 1 Jahr entspricht, wenn das Geld zu 10% p.a. angelegt werden kann. Daraus ergibt sich die Barwertregel.

## Endwert

Frage: Welchen Betrag erhält man in n Jahren, wenn man heute einen Betrag zum Zinssatz i anlegt?

Der Endwert ist der Wert einer heutigen Zahlung CF₀, die für n Jahre zum Zinssatz i angelegt werden kann. Umfasst dabei den ursprünglichen Anlagebetrag zuzüglich Zinsen und Zinseszinsen.

**EW_n = CF₀ · (1 + i)^n**

- EW_n = Endwert zum Zeitpunkt n
- CF₀ = Zahlung (Cash Flow) im Zeitpunkt n = 0 (Zeitpunkt der Einzahlung)
- i = Zinssatz (englisch: „interest rate")
- n = Laufzeit (Dauer der möglichen Zinserträge der Zahlung)
- (1 + i)^n = **Aufzinsungsfaktor**

Aufgabe (Folie 56): Frieda plant bereits heute die Abschlussparty für ihren Bachelorabschluss. Dafür hat sie zu Studienbeginn 1.000 € auf die Seite gelegt. Die Bank bietet ihr einen Zinssatz von 3% pro Jahr an. Mit welchem Kapital kann Frieda nach 3 Jahren für ihre Party rechnen?

## Barwert

Frage: Welchen Wert hat ein zukünftiger Zahlungsfluss zum heutigen Zeitpunkt bei einem möglichen Zinssatz i?

Der Barwert (BW₀) ist der heutige Wert eines zukünftigen Zahlungszuflusses CF_n. Zur Berechnung wird die zu ihrem Zeitwert angesetzte Zahlung mit dem Zinssatz (i) über die Laufzeit (n) abgezinst (diskontiert).

**BW₀ = CF_n / (1 + i)^n**

Damit beantwortet der Barwert die Frage, welchen Betrag ein Investor heute investieren muss, um nach n Jahren über das Endvermögen verfügen zu können.

- BW₀ = Barwert zum Zeitpunkt 0
- CF_n = Zahlung (Cash Flow) im Zeitpunkt n
- i = Zinssatz
- n = Laufzeit
- (1+i)^−n = **Abzinsungs- bzw. Diskontierungsfaktor**

Aufgabe (Folie 59): Welchen Barwert weist eine Zahlung auf, die am Ende des 8. Jahres in Höhe von 150.000 € geleistet wird? Der Kalkulationszinssatz beträgt 5%.

Quelle: Folien 52–59

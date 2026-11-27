# Lösung zu Aufgabe 1) — Beurteilung von Investitionen

Die Originallösung deckt nur Teil 1.) des Aufgabenblattes ab (Ausgangslage und Annahmen sind dort wiederholt, siehe `TASKS.md`).

## 1. Gewinnvergleichsrechnung

**Shop A**

| | | |
|---|---|---|
| Durchschnittlicher Erlös | 600.000 € | 12€ x 50.000 Stück |
| - Durchschn. variable Kosten | - 150.000 € | 3€ x 50.000 Stück |
| - Durchschn. fixe Kosten | - 20.000 € | Strom, Reinigung, Miete |
| - Durchschn. fixe Lohnkosten | - 100.000 € | |
| - Kalkulatorische* Abschreibung | - 150.000 € | => (500.000-50.000)/3 Jahre |
| - Kalkulatorische* Zinskosten | - 27.500 € | => (500.000+50.000)/2*(10% Zins) |
| **= Gewinn** | **= 152.500 €** | |

**Shop B**

| | | |
|---|---|---|
| Durchschnittlicher Erlös | 300.000 € | 10€ x 30.000 Stück |
| - Durchschn. variable Kosten | - 60.000 € | 2€ x 30.000 Stück |
| - Durchschn. fixe Kosten | - 10.000 € | Strom, Reinigung, Miete |
| - Durchschn. fixe Lohnkosten | - 30.000 € | |
| - Kalkulatorische* Abschreibung | - 110.000 € | => (250.000-30.000)/2 |
| - Kalkulatorische* Zinskosten | - 14.000 € | => (250.000+30.000)/2) *(10% Zins) |
| **= Gewinn** | **= 76.000 €** | |

\* Kalkulatorisch sind die Kosten deswegen, da die Werte von den bilanziellen (nach HGB) Werten abweichen können. Daher nennt man sie hier kalkulatorische Kosten, da diese für die Kalkulation (Kostenträgerrechnung) gebraucht werden.

Antwort: Damit sollte Shop A umgesetzt werden.

## 2. Rentabilitätsvergleichsrechnung

ROI = EBIT / durchschnittlich investiertes Kapital

EBIT* = Gewinn + Zinskosten + Steueraufwand — \* EBIT (Earnings Before Interest and Taxes)

Shop A:

- EBIT (A) = Gewinn: 152.500€ + Zinskosten 27.500€ + Steueraufwand 0€ = 180.000€
- Durchschnittlich investiertes Kapital (A) = (500.000€+50.000€)/2 = 275.000€
- ROI (A) = 180.000€/275.000€ = 65,5%

Shop B:

- EBIT (B) = 90.000€
- Durchschnittlich investiertes Kapital (B) = 140.000€
- ROI (B) = 90.000€/140.000€ = 64,3%

- Basierend auf dem ROI sollte in Shop A investiert werden.
- Investitionsentscheidungen, die rein auf der Rentabilität beruhen, können aufgrund von falschen Zukunftsannahmen oder aufgrund von falschen Annahmen bezüglich der Differenzinvestitionssumme zu Fehlentscheidungen führen. Beispielsweise sind Projekte mit 100€ Investition aber 50% Rentabilität sind i.d.R. schlechter, als Projekte mit 1 Mio € Investition und 20% Rentabilität, da der Gesamtwert dabei höher ist. Deshalb ist die Kapitalwertberechnung wichtig.

## 3. Kapitalwertregel

Die Lösung stellt die Teilaufgabe erweitert dar:

- a. Bestimmen Sie aus den geplanten Vorgängen die Cash Flows. Ordnen Sie diese auch als operative Cash Flows, Investitions Cash Flows oder Finanzierungs Cash Flows ein.
- b. Erstellen Sie eine Zahlungsplanung auf Basis der Cash Flows.
- c. Berechnen Sie den Barwert aller Cash Flows der Projekte.
- d. Berechnen Sie den Kapitalwert beider Projekte.
- e. Entscheiden Sie, welches Projekt durchgeführt werden soll.

### Lösung Kaffee A — Cash-Flow-Ermittlung (vereinfacht)

Operativer Cash Flow - direkte Ermittlung

| | |
|---|---|
| Umsatzerlöse (zahlungswirksam) | 600.000 |
| - Durchschnittliche variable Kosten (zw) | -150.000 |
| - Durchschnittliche fixe Kosten (zw) | -120.000 |
| **Operativer Cashflow** | **330.000** |

Operativer Cash Flow - indirekte Ermittlung

| | |
|---|---|
| Gewinn | 152.500 |
| + kalkl. Zinskosten | 27.500 |
| + kalk. Abschreibungen | 150.000 |
| **Operativer Cashflow** | **330.000 €** |

### Lösung Kaffee B — Cash-Flow-Ermittlung (vereinfacht)

Operativer Cash Flow - direkte Ermittlung

| | |
|---|---|
| Umsatzerlöse (zahlungswirksam) | 300.000 |
| - Durchschnittliche variable Kosten (zw) | -60.000 |
| - Durchschnittliche fixe Kosten (zw) | -40.000 |
| **Operativer Cashflow** | **200.000** |

Operativer Cash Flow - indirekte Ermittlung

| | |
|---|---|
| Gewinn | 76.000 |
| + kalkl. Zinskosten | 14.000 |
| + kalk. Abschreibungen | 110.000 |
| **Operativer Cashflow** | **200.000 €** |

### Shop A — Kapitalwertberechnung [in TEUR]

| Jahre | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| Cashflows aus Investitionstätigkeit | -500 | | | 50 |
| Cashflows aus operativem Geschäft | | 330 | 330 | 330 |
| **Gesamt Cashflow** | **-500** | **330** | **330** | **380** |
| Abzinsungsfaktor | 1 | 0,91 | 0,83 | 0,75 |
| Barwert | -500,0 | 300,3 | 273,9 | 285,0 |
| **Kapitalwert** | **359,2** | | | |

Für i = 10% ergibt sich

KW = −500 + 330/(1+0,1) + 330/(1+0,1)² + (330+50)/(1+0,1)³

KW = 358.226 €

Hinweis: In der Klausur wird jeweils angegeben, ob und auf welche Genauigkeit das Ergebnis zu runden ist.

### Shop B — Kapitalwertberechnung [in TEUR]

| Jahre | 0 | 1 | 2 |
|---|---|---|---|
| Cashflows aus Investitionstätigkeit | -250 | | 30 |
| Cashflows aus operativem Geschäft | | 200 | 200 |
| **Gesamt Cashflow** | **-250** | **200** | **230** |
| Abzinsungsfaktor | 1 | 0,91 | 0,83 |
| Barwert | -250,0 | 182,0 | 190,9 |
| **Kapitalwert** | **122,9** | | |

KW = −250 + 200/(1+0,1) + 230/(1+0,1)²

KW = 121.900,83 €

Ein Finanzierungs-Cash-Flow liegt in diesem Fall nicht vor. Ein Finanzierungscashflow liegt vor bei Zahlungsflüssen aus Finanzierungen von Eigen- oder Fremdkapital, also beispielsweise die Auszahlung eines Kredites für unser Kaffee.

- Es sollte in Shop A investiert werden, da dieses den höheren Kapitalwert aufweist.

## 4. Interne Zinsfußregel

Der Interne Zinsfuß (IZF) oder die Investitionsrendite (Internal Rate of Return, IRR) ist derjenige Zinssatz, für den der Kapitalwert (KW0) eines Projektes = 0 ist.

Für Kaffee A: 0 = −500 + 330/(1+i) + 330/(1+i)² + (330+50)/(1+i)³

Diese Gleichung ist manuell schwer lösbar. Verwenden Sie stattdessen einen Finanzrechner, Excel mit der Funktion „IKV" oder die Methode des Trials-and-Errors. Daraus ergibt sich ein interner Zinsfuß von i=46,48%.

Für Kaffee B: 0 = −250 + 200/(1+i) + 230/(1+i)²

- i) Substituiere (1+i) = x => 0 = −250 + 200/x + 230/x²
- ii) 0 = 250x² − 200x − 230
- iii) Mit der Mitternachtsformel ausrechnen und dabei nur die positive Lösung berücksichtigen und anschließend in (1+i) einsetzen
- iv) Führt zum Ergebnis: 43,92%

Mitternachtsformel: x(1,2) = (−b ± √(b² − 4ac)) / 2a

- Basierend auf dem internen Zinsfuß sollte in Shop A investiert werden.
- Der interne Zinsfuß kann durch Fehlentscheidungen bei sehr geringen absoluten Beträgen zu falschen Entscheidungen führen.

## 5. Amortisationsregel

Vereinfachte Amortisationsrechnung:

Investitionssumme / Cashflow = Amortisationszeit

- Amortisationszeit Kaffee A = 500.000€ / 330.000 € = 1,5 Jahre
- Amortisationszeit Kaffee B = 250.000€ / 200.000€ = 1,25 Jahre

\* Da es in manchen Perioden keinen operativen CF gibt, ist hier der Operative CF = Free CF.

- Basierend auf der Amortisationszeit sollte in das Kaffee B investiert werden, da sich die Investition hier schneller amortisiert.

## 6. Kritische Analyse

- a. Erläutern Sie, welche der o.g. Regeln die wichtigste ist und warum.
- b. Diskutieren Sie das Ergebnis insgesamt.

Die wichtigste Berechnungsmethode zum Vergleich von Investitionsalternativen ist die Kapitalwertmethode, da hier absolute Werte verglichen werden und die zeitliche Struktur der Cash-Flows berücksichtigt wird.

Quelle: `investition/origin/WDS25 - Finanzierung und Investition (SCS)/04 Übungsblätter/Lösung Aufgabe 1) Blatt 2/`

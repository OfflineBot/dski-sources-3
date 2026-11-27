# Kapitalwertmethode

## Definition

Der **Kapitalwert (KW₀)** eines Investitionsprojekts ist der Barwert sämtlicher Ein- und Auszahlungen einer Investition. Englisch: Net Present Value (NPV).

**KW₀ = CF₀/(1+i)⁰ + CF₁/(1+i)¹ + … + CF_n/(1+i)^n  ⇒  KW₀ = Σ (t=0 bis n) CF_t/(1+i)^t**

Im Fall von Investitionen besteht im Regelfall eine hohe Investitionsauszahlung I₀ am Beginn der Investition und eine hohe Restwertzahlung R_n bei Verkauf/Liquidation der Investition:

**KW₀ = −I₀ + Σ (t=1 bis n) CF_t/(1+i)^t + R_n/(1+i)^n**

- KW₀ = Kapitalwert im Zeitpunkt 0
- I₀ = Anschaffungsauszahlung in t₀
- CF_t = Cash Flow im Zeitpunkt t
- n = Nutzungsdauer
- i = Kalkulationszinssatz
- R_n = Restwert

**Kapitalwert = Barwert der Rückflüsse − Investitionsauszahlungen**

## Interpretation und Entscheidungskriterium

| Kapitalwert | Bedeutung |
|---|---|
| KW₀ > 0 | Vermögenszuwachs: Rendite des Investitionsprojektes liegt oberhalb des Kalkulationssatzes. **Investieren!** |
| KW₀ = 0 | Rendite des Investitionsprojektes entspricht dem Kalkulationssatz (Mindestverzinsung) |
| KW₀ < 0 | Vermögensminderung: Rendite des Investitionsprojektes liegt unterhalb des Kalkulationssatzes. **Nicht investieren!** |

Ist der Kapitalwert eines Projektes positiv, sollte in das Projekt investiert werden. Ist der Kapitalwert negativ, sollte auf keinen Fall investiert werden. Haben zwei Projekte beide einen positiven Kapitalwert, sollte in das Projekt mit dem höheren Kapitalwert investiert werden.

Ein positiver Kapitalwert bedeutet, dass ein Projekt/eine Investition den Unternehmenswert über die Mindestverzinsung hinaus erhöht hat. Es wird damit Wert geschaffen.

## Beispiel: Cleverle AG

Die Cleverle AG verfügt über 10 Mio. €. Die jährlichen Finanzierungskosten (Diskontierungszins) dafür sind 10%. Für das Geld gibt es zwei Investitionsalternativen:

- Anlage bei einer Bank für 4 Jahre bei einem Zinssatz von 10%.
- Investition in ein Projekt A mit einer Laufzeit von 4 Jahren.

| Jahr | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| Cash Flow Bank | -10 | 1 | 1 | 1 | +1 +10 |
| Cash Flow Projekt A | -10 | +3,8 | +3,8 | +3,8 | +3,8 +1 |

Projekt A als Zahlungsplan:

| Jahr | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| Inv. CF | -10 Mio | | | | 1 Mio. |
| Op. CF | | 3,8 Mio | 3,8 Mio | 3,8 Mio. | 3,8 Mio. |
| **Free Cash Flow** | **-10** | **3,8** | **3,8** | **3,8** | **4,8** |

KW₀ = −10 + 3,8/(1+0,1)¹ + 3,8/(1+0,1)² + 3,8/(1+0,1)³ + 4,8/(1+0,1)⁴ = **2,73 Mio.**

Entscheidungslogik: Wähle das Projekt mit dem höchsten Kapitalwert heute.

### Bedeutung des Kapitalwerts

1. Alternative: Investition des Geldes auf ein Bankkonto mit 10% Zinsen p.a. für 4 Jahre.
   - Wert des Geldes nach 4 Jahren: EW₄ = 10 Mio. · (1 + 0,1)⁴ = 14,64 Mio. €
   - Wert des Geldes heute: BW₀ = 14,64 / (1+0,1)⁴ = 10 Mio. €
2. Alternative: Investition in Projekt A.
   - Wert des Geldes nach 4 Jahren: EW₄ = 3,8 · (1+0,1)³ + 3,8 · (1+0,1)² + 3,8 · (1+0,1)¹ + 4,8 · (1+0,1)⁰ = 18,64 Mio. €
   - Wert des Geldes heute: BW₀ = 18,64 / (1+0,1)⁴ = 12,73

Differenz zwischen Barwert Projekt A und Barwert Bankkonto = 12,73 Mio. − 10 Mio. = **2,73 Mio. €**

Interpretation: Der Kapitalwert entspricht dem **Mehrwert der Investition in ein Projekt gegenüber der Investition auf ein Bankkonto** (oder auf ein Alternativprojekt). Der Diskontierungszins entspricht der Rendite einer Alternativinvestition.

## Kritische Analyse

**Vorteile**

- Der Kapitalwert basiert auf Cash-Flow statt auf Zahlen des Rechnungswesens (z.B. Gewinn oder Deckungsbeiträge). Daher ist der Barwert nicht abhängig von bilanziellen Spielräumen und kann schwerer manipuliert werden.
- Der Zeitwert des Geldes wird durch die Diskontierung des Cash-Flows einbezogen. Im Vergleich wird dies bei der reinen Betrachtung der Gewinn- und Verlustrechnung aus dem Rechnungswesen oder der Kosten- und Leistungsrechnung nicht betrachtet.

**Nachteile**

- In der Unternehmenspraxis werden häufig Rentabilitätskennzahlen nicht in absoluten Zahlen verwendet, sondern in relativen (z.B. „Der Return on Investment ist 15%"). Der Kapitalwert ist eine absolute Kennzahl, die daher nicht für einen solchen Vergleich herangezogen werden kann.

Quelle: Folien 60–67

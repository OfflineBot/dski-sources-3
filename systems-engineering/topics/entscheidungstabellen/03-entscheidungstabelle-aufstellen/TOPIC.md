# Hier kann uns eine Entscheidungstabelle helfen, zu klären, welche Zahlungsweisen unter welchen Bedingungen zulässig sind

| ET #001 | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| B1: Kunde gesperrt | J | J | J | J | N | N | N | N |
| B2: Offene Rechnungen > 1000 EUR | J | J | N | N | J | J | N | N |
| B4: Einwandfreies Zahlungsverhalten | J | N | J | N | J | N | J | N |
| A1: Verweigerung | X | X | X | X | | | | |
| A2: Bankeinzug | | | | | X | X | | X |
| A3: Nachnahme | | | | | | | X | |

- Bedingungsteil: B1, B2, B4
- Aktionsteil: A1, A2, A3
- Regelteil: R1, R2, R3, R4, R5, R6, R7, R8

## Konsolidierung

Eine Entscheidungstabelle ist konsolidierbar, wenn mehrere Regeln zu einer zusammengefasst werden können. Hier: R1-R4

| ET #001 | R1 | R5 | R6 | R7 | R8 |
| --- | --- | --- | --- | --- | --- |
| B1: Kunde gesperrt | J | N | N | N | N |
| B2: Offene Rechnungen > 1000 EUR | - | J | J | N | N |
| B4: Einwandfreies Zahlungsverhalten | - | J | N | J | N |
| A1: Verweigerung | X | | | | |
| A2: Bankeinzug | | X | X | | X |
| A3: Nachnahme | | | | X | |

Frage: Kann man noch weitere Regeln zusammenfasen

## Weitere Regeln

**Redundanzfreiheit**

| | R1 | R2 |
| --- | --- | --- |
| B1 | J | J |
| B2 | N | - |
| B3 | N | N |
| A1 | X | X |
| A2 | X | X |

R1 braucht es nicht, da R2 diese Regel schon beinhaltet für B2 = "N"

**Widerspruchsfreiheit/Konsistenz**

| | R1 | R2 |
| --- | --- | --- |
| B1 | J | J |
| B2 | N | N |
| B3 | - | N |
| A1 | X | X |
| A2 | X | |

R1 steht bei B3 = "N" mit R2 im Widerspruch, denn R1 hat A1 und A2 als Aktion, R2 aber nur A1.

Quelle: systems-engineering/origin/WDS125 - Systems Engineering (BäM)/12 LE 9_ Entscheidungstabellen - Modellierung von stark regelbehafteten Anforderungen/Folien der Lerneinheit/11.RE-ET.pdf, Folien 10–12

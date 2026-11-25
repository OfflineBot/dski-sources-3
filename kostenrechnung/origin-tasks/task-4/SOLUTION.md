# Lösung: Aufgabe A2 35 Betriebsabrechnungsbogen (BAB) – Eine Übersicht

## BAB Lösung

Kopf des Bogens: Die acht Spalten Allg. KSt bis Verw.+Vert. stehen unter "Kostenstellen", die Spalten Fert. Hilfskst. I bis Fert. St. C unter "Fertigungsbereich".

| Kostenarten | Gesamt | Allg. KSt | Fert. Hilfskst. I | Fert. Hilfskst. II | Fert. St. A | Fert. St. B | Fert. St. C | Mat. St. | Verw.+Vert. | Kontrolle |
|---|---|---|---|---|---|---|---|---|---|---|
| Hilfslöhne | 3.000 | 300 | 150 | 150 | 450 | 600 | 750 | 450 | 150 | 3.000 |
| Strom | 520 | 40 | 40 | 40 | 80 | 80 | 80 | 80 | 80 | 520 |
| kalk. Zinsen | 980 | 60 | 120 | 80 | 280 | 210 | 140 | 20 | 70 | 980 |
| sonstige Kosten | 1.600 | 200 | 200 | 200 | 200 | 200 | 200 | 200 | 200 | 1.600 |
| **PSK (Summe I)** | **6.100** | 600 | 510 | 470 | 1.010 | 1.090 | 1.170 | 750 | 500 | **6.100** |
| Umlage Allgemeine KSt | | -600 | 50 | 100 | 100 | 150 | 50 | 50 | 100 | 0 |
| Umlage FHSt I | | | -560 | 80 | 160 | 80 | 240 | | | 0 |
| Umlage FHSt II | | | | -650 | 300 | 200 | 150 | | | 0 |
| **SSK (Summe II)** | | -600 | -510 | -470 | 560 | 430 | 440 | 50 | 100 | **0** |
| **Gesamtstellenkosten** | **6.100** | Null | Null | Null | 1.570 | 1.520 | 1.610 | 800 | 600 | **6.100** |
| Fertigungslöhne | 2.500 | | | | 1.000 | 800 | 700 | | | |
| Fertigungsmaterial | 4.000 | | | | | | | 4.000 | | |
| Herstellkosten | | | | | | | | | | |
| Zuschlagssätze (IST) | | | | | 157% | 190% | 230% | 20% | 5 | |
| Zuschlagssätze (Soll) | | | | | 150% | 200% | 250% | 10% | 10% | |
| Verrechnete Gemeinkosten | | | | | 1.500 | 1.600 | 1.750 | 400 | 1.175 | |
| Überdeckung | | | | | | 80 | 140 | | 575 | |
| Unterdeckung | | | | | -70 | | | -400 | | |

Die Zeile Herstellkosten ist auch in der Lösung leer. Bei Zuschlagssätze (IST) steht für Verw.+Vert. "5" ohne Prozentzeichen.

## Verteilungsschlüssel

Hilfskostenstellen: Allg. KSt, Fert. Hilfskst. I, Fert. Hilfskst. II. Hauptkostenstellen: Fert. St. A, Fert. St. B, Fert. St. C, Mat. St., Verw.+Vert.

| Verteilungsschlüssel | Gesamt | Allg. KSt | Fert. Hilfskst. I | Fert. Hilfskst. II | Fert. St. A | Fert. St. B | Fert. St. C | Mat. St. | Verw.+Vert. |
|---|---|---|---|---|---|---|---|---|---|
| Hilfslöhne | 20 | 2 | 1 | 1 | 3 | 4 | 5 | 3 | 1 |
| Strom | 13 | 1 | 1 | 1 | 2 | 2 | 2 | 2 | 2 |
| kalk. Zinsen (Vermögen) | 12% | 6.000 | 12.000 | 8.000 | 28.000 | 21.000 | 14.000 | 2.000 | 7.000 |
| sonstige Kosten | 8 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |

## Kalkulation Lösung

Die Zeichen + und = in der ersten Spalte stehen so wie im Formular (von außen nach innen).

| | Position | Kürzel | Angebotskalkulation (Soll): Satz | Angebotskalkulation (Soll): Betrag | Nachkalkulation (Ist): Satz | Nachkalkulation (Ist): Betrag | Soll/Ist-Vergleich |
|---|---|---|---|---|---|---|---|
| | Materialeinzelkosten | (MEK) | | 4.000 | | 4.000 | |
| + | Materialgemeinkosten | (MGK) | 10% | 400 | 20% | 800 | |
| + = | **Materialkosten** | **(MK)** | | **4.400** | | **4.800** | **-400** |
| | Fertigunslöhne A | (FL A) | | 1.000 | | 1.000 | |
| + | Fertigungsgemeinkosten A | (FGK A) | 150% | 1.500 | 157% | 1.570 | |
| + = | Fertigungskosten A | (FK A) | | 2.500 | | 2.570 | -70 |
| | Fertigunslöhne B | (FL B) | | 800 | | 800 | |
| + | Fertigungsgemeinkosten B | (FGK B) | 200% | 1.600 | 190% | 1.520 | |
| + = | Fertigungskosten B | (FK B) | | 2.400 | | 2.320 | 80 |
| | Fertigunslöhne C | (FL C) | | 700 | | 700 | |
| + | Fertigungsgemeinkosten C | (FGK C) | 250% | 1.750 | 230% | 1.610 | |
| + = | Fertigungskosten C | (FK C) | | 2.450 | | 2.310 | 140 |
| + = | **Fertigungskosten** | **(FK)** | | **7.350** | | **7.200** | **150** |
| = | **Herstellkosten der Produktion** | **(HK)** | | **11.750** | | **12.000** | **-250** |
| = | **Herstellkosten des Vertriebs (Abgesetzte Leistung)** | | | | | | |
| + | Verwaltungseinzelkosten | (VWEK) | | | | | |
| + | Verwaltungsgemeinkosten | (VWGK) | 10% | 1.175 | 5% | 600 | 575 |
| + = | Verwaltungs- und Vertriebskosten | (VVK) | | | | | |
| = | **Selbstkosten** | **(SK)** | | **12.925** | | **12.600** | **325** |

## Handschriftliche Rechenhinweise des Profs

Auf der Aufgabenfolie:

- Bei Angabe 1 (Hilfslöhne): "/ Σ 20" und "3000 / 20 = 150" (Vorjahr)
- Bei Angabe 3 (kalkulatorische Zinsen): "12 %" eingekreist, darunter "60"; daneben "1 % pro Monat" (Vorjahr)
- Bei Angabe 5 (Allgemeine Kostenstelle): "/ Σ 12" und "600 / 12 = 50" (Vorjahr)
- Gelb markiert: "der Hilfslöhne", "Schlüssel: 2 : 1 : 1 : 3 : 4 : 5 : 3 : 1", "gebundene Vermögen", die ganze Angabe 5 (Vorjahr)

Auf der Folie BAB Leer:

- "3.000" (Hilfslöhne, Gesamt) gelb markiert (Vorjahr)

Auf der Folie BAB Lösung:

- "150" mit Linie auf Hilfslöhne Gesamt 3.000 (gelb markiert) (Vorjahr)
- "1 % geb. Vermögen" mit Linie auf die eingekreiste 60 (kalk. Zinsen, Allg. KSt) (Vorjahr)
- Neben den Beträgen der Zeile Hilfslöhne die Schlüsselzahlen: 2, 1, 1, 3, 4, 5, 3, 1 (Vorjahr)
- Neben den Beträgen der Zeile Umlage Allgemeine KSt (50 bis 100) die Schlüsselzahlen: 1, 2, 2, 3, 1, 1, 2 (Vorjahr)
- Rechts neben der Spalte Kontrolle: "Schlüssel", darunter ein zweites Wort [unleserlich] (Vorjahr)
- "Herstellkosten" gelb markiert (Vorjahr)

Auf den Folien Kalkulation Leer und Kalkulation Lösung steht keine Handschrift.

Quelle: kostenrechnung/origin/mitschriebt_3_von_5_aktuell.pdf, Folien 74, 76

Vorjahr: kostenrechnung/origin/mitschrieb_letzte_jahr.pdf, Folien 75-79

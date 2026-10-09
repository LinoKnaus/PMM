# Lösung — Binomialverteilung (KM5-01)

Aufgabenstellung: siehe [`PROMPT.md`](PROMPT.md).

Gegeben: Ausschussquote `p = 0.05`, Stichprobe `n = 20`.
Erwartungswert `np = 20 * 0.05 = 1` defektes Teil pro Stichprobe.

## 1. Wahrscheinlichkeiten für 0, 1, 2 und 3 defekte Teile

| k (defekt) | P(X = k) |
| --- | --- |
| 0 | 0.358486 |
| 1 | 0.377354 (häufigster Fall) |
| 2 | 0.188677 |
| 3 | 0.059582 |

Zusammen: `0.984098` — nur rund **1.6 %** haben 4 oder mehr Defekte.

## 2. Form der Verteilung

Die Verteilung ist **rechtsschief mit einem Gipfel bei `k = 1`** (der
Erwartungswert): links steil, rechts ein schnell abklingender Schwanz,
ab `k = 5` praktisch null.

## 3. Warum ist `(0 über 0) = 1`?

Weil es **genau einen Weg** gibt, aus null Versuchen null Erfolge
auszuwählen — den leeren Weg (gar nichts auswählen). Die Anzahl der
Teilmengen der leeren Menge ist 1 (nur die leere Menge selbst). Die
Formel bestätigt es: `0! / (0! * 0!) = 1 / (1 * 1) = 1`. Für `n = 0`,
`k = 0` liefert die Binomialformel
`P(X = 0) = 1 * p^0 * (1 - p)^0 = 1`.

## R-Skript

```r
# Hausaufgabe KM5-01 — Binomialverteilung am Fertigungsszenario
# p = 0.05 Ausschuss, n = 20 geprüfte Teile

p_ausschuss <- 0.05
n_teile <- 20

# --- 1. Wahrscheinlichkeiten für 0, 1, 2, 3 Defekte -------------
dbinom(0, size = n_teile, prob = p_ausschuss)
# → 0.3584859   — kein Teil defekt

dbinom(1, size = n_teile, prob = p_ausschuss)
# → 0.3773536   — genau ein Teil defekt (der häufigste Fall)

dbinom(2, size = n_teile, prob = p_ausschuss)
# → 0.1886768   — genau zwei Teile defekt

dbinom(3, size = n_teile, prob = p_ausschuss)
# → 0.0595821   — genau drei Teile defekt

# Kontrolle: die vier Fälle zusammen
sum(dbinom(0:3, size = n_teile, prob = p_ausschuss))
# → 0.9840984   — rund 98 %, nur 1.6 % haben vier oder mehr

# --- 2. Die ganze Verteilung als Balkenbild ---------------------
barplot(dbinom(0:n_teile, size = n_teile, prob = p_ausschuss),
        names.arg = 0:n_teile,
        xlab = "Anzahl defekter Teile (k)",
        ylab = "Wahrscheinlichkeit P(X = k)",
        main = "Binomialverteilung: n = 20, p = 0.05")
# Form: rechtsschief, Gipfel bei k = 1, langer flacher Schwanz
#       nach rechts (ab k = 5 praktisch null)

# --- 3. Warum (0 über 0) = 1? -----------------------------------
# Aus null Versuchen gibt es genau einen Weg mit null Erfolgen:
# den leeren Weg. 0! / (0! * 0!) = 1.
choose(0, 0)
# → 1
```

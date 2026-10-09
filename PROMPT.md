# Hausaufgabe — Binomialverteilung (KM5-01)

**Quelle:** Lektion `KM5-01 — Binomialkoeffizient & Pascalsches Dreieck`,
Abschnitt „Aufgabe" (`4ahwit-y/2026-10-02-binomialkoeffizient-pascalsches-dreieck/lesson.html`)

## Aufgabe

Wende die Binomialverteilung auf ein eigenes Fertigungsszenario an:

1. Nimm eine Ausschussquote `p = 0.05` und eine Stichprobe von `n = 20`
   Teilen. Berechne mit `dbinom` die Wahrscheinlichkeit für 0, 1, 2 und 3
   defekte Teile.
2. Zeichne die ganze Verteilung mit
   `barplot(dbinom(0:20, 20, 0.05))` und beschreibe die Form in einem
   Satz.
3. **Erklärung:** Warum ist `(0 über 0) = 1`? Argumentiere über die
   Anzahl der Wege.

**Abgabe:** R-Skript + kurze Antworten als Commit in deinem PMM-Repo.

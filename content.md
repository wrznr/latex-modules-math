layout: true
  
<div class="my-header"></div>

<div class="my-footer">
  <table>
    <tr>
      <td style="text-align:right">Sächsische Landesbibliothek – Staats- und Universitätsbibliothek</td>
      <td>19. Januar 2026</td>
      <td style="text-align:right"><a href="https://www.slub-dresden.de/">www.slub-dresden.de</a></td>
    </tr>
    <tr>
      <td style="text-align:right">Referat 4.3</td>
      <td />
    </tr>
  </table>
</div>

<div class="my-title-footer">
  <table>
    <tr>
      <td style="text-align:left"><b>Kay-Michael Würzner</b></td>
    </tr>
    <tr>
      <td style="text-align:left">Referat 4.3</td>
    </tr>
    <tr>
      <td style="font-size:8pt"><b>19. Januar 2026</b></td>
    </tr>
    <tr>
      <td style="font-size:8pt">LaTeX-Modul: Formeln</td>
    </tr>
  </table>
</div>

---

class: title-slide
count: false

# Mathematische Formeln in LaTeX
## Grundlagen, Umgebungen und Typografie

---

# Agenda

1. Wichtige Pakete & Ressourcen
2. Inline vs. Display Math
3. Zentrale Umgebungen (`equation`, `align`, `multline`)
4. Grundlegende Elemente (Brüche, Matrizen, Symbole)
5. Spezialfälle: Einheiten & Theoreme
6. **Interaktiver Teil & Übungen**

---

class: part-slide
count: false

# 1. Wichtige Pakete & Ressourcen

---

# Der Standard: AMS-Pakete

Standard für fast alle mathematischen Anwendungen Pakete der **American Mathematical Society (AMS)**

```latex
\usepackage{amsmath}  % Umgebungen für Formeln
\usepackage{amssymb}  % Zusätzliche Symbole
\usepackage{amsthm}   % Umgebungen für Sätze/Theoreme
```

Weitere Empfehlungen:
* `mathtools`: Erweiterung von amsmath (Layout-Tricks)
* `siunitx`: Für physikalische Einheiten (Wichtig für Nicht-Mathematiker!)
* [Short Math Guide (CTAN)](https://tug.ctan.org/info/short-math-guide/short-math-guide.pdf)
* [AMS Styleguide (Kap. 13)](https://www.ams.org/arc/styleguide/index.html)

---

class: part-slide
count: false

# 2. Inline vs. Display Math

---

# Zwei Modi der Darstellung

**1. Inline Math (im Fließtext)**
* Eingebettet in den Text.
* Symbole sind oft kleiner, Indizes rücken seitlich heran.
* Eingabe mit `$ ... $` oder `\( ... \)`.

**2. Display Math (Abgesetzt)**
* Steht in einer eigenen Zeile, zentriert.
* Symbole (Summen, Integrale) entfalten volle Größe.
* Eingabe mit `\[ ... \]` oder Umgebungen wie `equation`.

---

# Beispiel

* Inline: $\sum_{i=1}^n i$ sieht kompakt aus.
* Display:
    $$\sum_{i=1}^n i$$

---

class: part-slide
count: false

# 3. Zentrale Umgebungen

---

# Einzelne Gleichungen: `equation`

Für einzelne, nummerierte Gleichungen:

```latex
\begin{equation}
  E = mc^2 \label{eq:einstein}
\end{equation}
```

* Referenzierung im Text mit `\eqref{eq:einstein}`
* **ohne** Nummerierung: `\begin{equation*} ... \end{equation*}` (benötigt `amsmath`)

---

# Mehrzeilig & Ausgerichtet: `align`

Der Standard für mehrzeilige Herleitungen. Ausrichtung am `&` Zeichen.

```latex
\begin{align}
  f(x) &= (x+a)(x+b) \\
       &= x^2 + xb + ax + ab \\
       &= x^2 + x(a+b) + ab
\end{align}
```

* `&`: Ausrichtungsmarker (üblicherweise vor dem Gleichheitszeichen)
* `\\`: Zeilenumbruch
* für jede Zeile eine Nummer (unterdrücken mit `\nonumber` oder `align*`)

---

class: part-slide

# Many thanks for your attention!

<center>
<a href="https://wrznr.github.io/slide-template/">wrznr.github.io/latex-module-math</a>
</center>

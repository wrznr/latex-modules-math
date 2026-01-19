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

# Lange Gleichungen: `multline`

Formel zu lang für eine Zeile, aber ohne logische Ausrichtung am Gleichheitszeichen

```latex
\begin{multline}
  p(x) = 3x^6 + 14x^5 + 590x^4 + 19x^3 \\ 
         - 12x^2 - 39x + 22
\end{multline}
```

* erste Zeile: linksbündig
* letzte Zeile: rechtsbündig
* mittlere Zeilen: zentriert

---

class: part-slide
count: false

# 4. Grundlegende Elemente

---

**Brüche:**
```latex
\frac{Zähler}{Nenner}  % Normal
\dfrac{...}{...}       % Erzwingt Display-Größe
\tfrac{...}{...}       % Erzwingt Text-Größe
```

**Matrizen:** (benötigt `amsmath`)
```latex
\begin{pmatrix} a & b \\ c & d \end{pmatrix}  % Runde Klammern
\begin{bmatrix} a & b \\ c & d \end{bmatrix}  % Eckige Klammern
```
* Spaltentrenner: `&`
* Zeilenumbruch: `\\`

---

# Indizes, Exponenten & Griechisch

* **Subskript (Index):** `x_{12}` (`{}` bei mehr als einem Zeichen!)
* **Superskript (Exponent):** `x^{2}`
* **Griechisch:** * Klein: `\alpha`, `\beta`, `\gamma`, `\pi`
    * Groß: `\Gamma`, `\Pi`, `\Omega`

**Wichtig:** Griechische Buchstaben funktionieren nur im Mathe-Modus (`$ \alpha $`).

---

class: part-slide
count: false

# 5. Spezialfälle

---

# Einheiten mit `siunitx`

```latex
\usepackage{siunitx}
...
Die Geschwindigkeit beträgt \qty{120}{\kilo\metre\per\hour}.
Eine Länge von \qty{5e-9}{\meter}.
```

* Korrektes Spacing zwischen Zahl und Einheit.
* Einheitliche Typografie (aufrechtes "m" für Meter, kursives Variablen-$m$).

---

# Theoreme & Sätze (Enunciations)

**In der Präambel:**
```latex
\usepackage{amsthm}
\newtheorem{satz}{Satz}
\newtheorem{lemma}[satz]{Lemma}
```

**Im Dokument:**
```latex
\begin{satz}[Pythagoras]
  Im rechtwinkligen Dreieck gilt $a^2 + b^2 = c^2$.
\end{satz}

\begin{proof}
  Beweis hier... \qed
\end{proof}
```

---

class: part-slide
count: false

# 6. Interaktiver Teil

---

# Aufgabe 1: Einfache Formel

Setzen Sie folgende Formel in LaTeX (nutzen Sie `equation`):

$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}$$

**Tipps:**
* Paket `amsmath` notwendig?
* Befehle: `\frac`, `\sqrt`, `\pi`, `e^...`, `\left( ... \right)`

---

# Aufgabe 2: Ausrichtung

Setzen Sie folgende Herleitung mit `align*` (ohne Nummern):

$$
\begin{aligned}
(a+b)^2 &= (a+b)(a+b) \\\\
        &= a^2 + ab + ba + b^2 \\\\
        &= a^2 + 2ab + b^2
\end{aligned}
$$

**Achten Sie auf:**
* Wo muss das `&` stehen?
* Wie erzwingt man den Zeilenumbruch?

---

# Aufgabe 3: Matrizen & Einheiten

1.  Erstellen Sie eine 2x2 Matrix $A$ mit den Werten 1, 0 und 0, 1 (Einheitsmatrix).
2.  Schreiben Sie einen Satz mit `siunitx`: „Die Erdbeschleunigung beträgt ca. 9,81 m/s².“

---

class: part-slide

# Many thanks for your attention!

<center>
<a href="https://wrznr.github.io/slide-template/">wrznr.github.io/latex-module-math</a>
</center>

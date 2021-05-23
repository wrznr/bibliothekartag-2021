layout: true
  
<div class="my-header"></div>

<div class="my-footer">
  <table>
    <tr>
      <td style="text-align:right">Sächsische Landesbibliothek – Staats- und Universitätsbibliothek</td>
      <td>Date</td>
      <td style="text-align:right"><a href="https://www.slub-dresden.de/">www.slub-dresden.de</a></td>
    </tr>
    <tr>
      <td style="text-align:right">Referat 2.5</td>
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
      <td style="text-align:left">Referat 2.5</td>
    </tr>
    <tr>
      <td style="font-size:8pt"><b>Date</b></td>
    </tr>
    <tr>
      <td style="font-size:8pt">Event</td>
    </tr>
  </table>
</div>

---

class: title-slide
count: false

# Title
## Subtitle

---

# Overview

- Section 1
  + Subsection 1
- Section 2

---

class: part-slide
count: false

# Topic 1

---

### Transkriptionsrichtlinien

- Orientierung an DTA / OCR-D **GT-Level 2**  
  * bester Kompromiss aus Aufwand und Genauigkeit
  * häufige Eingabe von Sonderzeichen (`ſ ꝛ aͤ oͤ uͤ  — ⸗` …)

...

---

## Vorgehen Datenbereitstellung

1. OCR-Workflow
2. Extraktion von .xslx-Dateien
   - 1 Datei pro Seite
   - 1 Zeile pro Textzeile
3. Verteilung an je 2 Bearbeiter
4. Import des Rücklaufs
   - Textnormalisierung (automatische Nachkorrektur; optional)
   - Double-Keying zur Qualitätskontrolle
   - Konfliktbereinigung (manuelle Nachkorrektur; optional)
5. Export Line-GT (Format für tesstrain/ocropus/kraken/...)

---

### Textnormalisierung

- automatische Ersetzung bestimmter Muster zur Bereinigung von
  * häufigen Flüchtigkeitsfehlern
  * systematischen Abweichungen (wie Konventionen zu Interpunktion)
- Erhöhung der Ausbeute, Vermeidung von Unterrepräsentation
- abhängig vom Material (ohne/mit/gemischt `aͤ oͤ uͤ `, `ſ`, `ß`, `⸗`, `,` …)

- Beispiele:
  * `r" ⸗ "→"⸗"` `r"ä"→"aͤ"` `r"[=-]$"→"⸗"` (Beispielbild loskiel ...)
  * `r" /"→"/"` `r"/(?=\S)"→"/ "` (Beispielbild ryff ...)

---

## Ergebnisse Datenbereitstellung

- Umfang (vorläufig):
  * 18 Bearbeiter
  * 20 Werke à ?? Zeilen (vollständig) → ?? (vorausgewählt) → ?? (korrigiert) → ?? (übereinstimmend)
  * CER OCR ...

---

## Ergebnisse Training

| **Werk** | **CER vorher** | **CER nachher** |
| --- | --- | --- |
| `krankenkochbuch` | ?? | ?? |
| ... | ... | ... |
| gesamt | ?? | ?? |


---

class: part-slide

# Many thanks for your attention!

<center>
<a href="https://wrznr.github.io/slide-template/">wrznr.github.io/slide-template</a>
</center>

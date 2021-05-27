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
      <td style="text-align:right">Referate 4.3 & 2.5</td>
      <td />
    </tr>
  </table>
</div>

<div class="my-title-footer">
  <table>
    <tr>
      <td style="text-align:left"><b>Kay-Michael Würzner</b></td>
      <td style="text-align:left"><b>Robert Sachunsky</b></td>
    </tr>
    <tr>
      <td style="text-align:left">Referat Open Science</td>
      <td style="text-align:left">Referat Digitale Objekte</td>
    </tr>
    <tr>
      <td style="font-size:8pt"><b>17. Juni 2021</b></td>
    </tr>
    <tr>
      <td style="font-size:8pt">109. Bibliothekartag</td>
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

1. OCR-D-Workflow (manuell optimiert je Werk)
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
- zur Erhöhung der Ausbeute, Vermeidung von Unterrepräsentation
- abhängig vom Material (ohne/mit/gemischt `aͤ oͤ uͤ `, `ſ`, `ß`, `⸗`, `,` …)

- Beispiele:
  * `r" ⸗ "→"⸗"` `r"ä"→"aͤ"` `r"[=-]$"→"⸗"`  
    ![Beispielbild Loskiel](./img/FILE_0007_GT_Page1_Block3_Page1_Block3_line0003.bin.png)  
    <tt>Bruͤder<u> = </u>Unit<u>ä</u>t iſt die unter die Indianer in</tt>
  * `r" /"→"/"` `r"/(?=\S)"→"/ "`  
    ![Beispielbild Ryff](./img/FILE_0408_GT_Page1_Block1_Page1_Block1_line0023.bin.png)
    <tt>bel<u> </u>/ Knoblauch<u> </u>/ Senff<u> </u>/ Eſſig<u> </u>/ Saltz vñ</tt>

---

## Ergebnisse Datenbereitstellung

<table border="0" cellspacing="0" cellpadding="0">
  <tr style="vertical-align:top">
    <td>
      
- Umfang (vorläufig):
  * 18 Bearbeiter, ~200 Emails
  * 16 Werke, 10 mit Double-Keying
  * → 6473 Seiten (vollständig)
  * → 199317 Zeilen (vollständig)
  * → 477 Seiten (vorausgewählt)
  * → 20808 Zeilen (vorausgewählt)
  * → 14909 Zeilen (korrigiert)
  * → 13335 Zeilen (übereinstimmend)
    
  </td>
    <td>
      
- Inter-Annotator-Agreement
  * 89% Zeilen (Ausbeute Double-Keying)
  * 99.7% Zeichen (= 0.3% CER)
- Genauigkeit der Baseline-OCR
  * 97.2% Zeichen (= 2.8% CER)
  * 98.8% Zeichen (= 1.2% CER): nur Fraktur (`GT4HistOCR+frk+Fraktur`)
  * 96.2% Zeichen (= 3.8% CER): nur Antiqua (`deu+Latin`)

    </td>
  </tr>
</table>


---

## Ergebnisse Training

- werkspezifisches Finetuning
- generisches Finetuning (nur Fraktur)
- generisches Finetuning (nur Antiqua)
- generisches Finetuning (alles)
- generisches Baseline-Training (alles)

| **Werk** | **CER vorher** | **CER nachher** |
| --- | --- | --- |
| `krankenkochbuch` | ?? | ?? |
| ... | ... | ... |
| gesamt | ?? | ?? |


---

class: part-slide

# Vielen Dank für Ihre Aufmerksamkeit!

<center>
<a href="https://wrznr.github.io/bibliothekartag-2021">wrznr.github.io/bibliothekartag-2021</a>
</center>

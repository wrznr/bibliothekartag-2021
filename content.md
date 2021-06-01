layout: true
  
<div class="my-header"></div>

<div class="my-footer">
  <table>
    <tr>
      <td style="text-align:right">Sächsische Landesbibliothek – Staats- und Universitätsbibliothek</td>
      <td>109. Bibliothekartag</td>
      <td style="text-align:right"><a href="https://www.slub-dresden.de/">www.slub-dresden.de</a></td>
    </tr>
    <tr>
      <td style="text-align:right">Referate 4.3 & 2.5</td>
      <td>17. Juni 2021</td>
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

# Kollaborative Erstellung von Trainingsmaterialien für OCR
## Ein Werkstattbericht

---

# Überblick

- Prinzipien OCR
- Datenvorbereitung
- Transkription
- Training
- Diskussion

---

# Danksagung

---

# Überblick

1. OCR-D-Workflow (manuell optimiert je Werk)
2. Extraktion von .xslx-Dateien
   - 1 Datei pro Seite
   - 1 Zeile pro Textzeile
3. Verteilung an je 2 Bearbeiter
4. Import des Rücklaufs
   - Textnormalisierung (automatische Nachkorrektur; optional)
   - Double-Keying zur Qualitätskontrolle
   - Konfliktbereinigung (manuelle Nachkorrektur; optional)
5. Export Zeilen-GT
   - Format für tesstrain/ocropus/kraken/…
   - Publikation auf [Github](https://github.com/slub/slub_ocr_gt)
6. Training und Experimente

---

class: part-slide

# Prinzipien OCR

---

class: part-slide

# Datenvorbereitung

- Werkauswahl
- OCR-Workflow
- Ergebnisse

---

# Werkauswahl

---

# OCR-Workflow

- Konfiguration und Prozessierung mit [OCR-D](https://ocr-d.de)
- meist:
  * Binarisierung: [SBB](https://github.com/qurator-spk/sbb_binarization) (neuronal)
  * Cropping: [Ocropus](https://github.com/OCR-D/ocrd_anybaseocr) (regelbas.)
  * Deskewing: [Ocropus](https://github.com/cisocrgroup/ocrd_cis/) / [Tesseract](https://github.com/OCR-D/ocrd_tesserocr) (regelbas.)
  * Segmentierung: [Ocropus](https://github.com/cisocrgroup/ocrd_cis/) / [Tesseract](https://github.com/OCR-D/ocrd_tesserocr) (regelbas.)
  * Dewarping: [Ocropus](https://github.com/cisocrgroup/ocrd_cis/) (regelbas.)
  * Erkennung: [Tesseract](https://github.com/OCR-D/ocrd_tesserocr) (neuronal)
- Anpassung je nach Material und Sprachen
- Rückgriff auf existierende, bestpassende OCR-Modelle

---

class: part-slide

# Transkription

- Annotationsumgebung
- Transkriptionsrichtlinien
- Textnormalisierung
- Ergebnisse

---

# Annotationsumgebung

- Excel / LibreOffice Calc
  * Offline
  * Rechtschreibkontrolle
  * ...
- 1 Tabelle pro Seite mit 1 Zeile pro Textzeile und Spalten für:
  * ID (aus PAGE-XML)
  * Text (aus OCR)
  * Status (offen/fertig/fehlerhaft)
  * Bild (aus Binarisierung und Zeilensegmentierung)  
    Klick → Faksimile (DFG-Viewer)

---

# Annotationsumgebung – Ansicht

![screenshot](./img/excel-ocr-gt-annotation.png)

---

# Transkriptionsrichtlinien

- Orientierung an [DTA](https://www.deutschestextarchiv.de/doku/basisformat/transkription.html) / [OCR-D](https://ocr-d.de/de/gt-guidelines/trans/transkription.html) **GT-Level 2**  
  * bester Kompromiss aus Aufwand und Genauigkeit
  * häufige Eingabe von Sonderzeichen (`ſ ꝛ aͤ oͤ uͤ  — ⸗` …)
  * viele verbleibende Unklarheiten...

<!-- Intranetdialog -->

...

---

# Textnormalisierung

- automatische Ersetzung bestimmter Muster zur Bereinigung von
  * typischen Flüchtigkeitsfehlern
  * systematischen Abweichungen (wie Konventionen zu Interpunktion)
- Erhöhung der Ausbeute, Vermeidung von Unterrepräsentation
  * Gerade schwierige Daten sind wertvoll für das Training!
- abhängig vom Material (manchmal/immer ohne/mit `aͤ` `oͤ` `uͤ` `ſ` `ß` `⸗` `,` …) <!-- oder gemischt -->
- Beispiele:  

| `r" ⸗ "` → `"⸗"` <br/> `r"ä"` → `"aͤ"` <br/> `r"[=-]$"` → `"⸗"` | `r" /"` → `"/"` <br/> `r"/(?=\S)"` → `"/ "` |
| --- | --- |
| ![Beispielbild Loskiel](./img/FILE_0007_GT_Page1_Block3_Page1_Block3_line0003.bin.png) | ![Beispielbild Ryff](./img/FILE_0408_GT_Page1_Block1_Page1_Block1_line0023.bin.png) |
| Bruͤder<u> = </u>Unit<u>ä</u>t iſt die unter die Indianer in | bel<u> </u>/ Knoblauch<u> </u>/ Senff<u> </u>/ Eſſig<u> </u>/ Saltz vñ |

---

# Ergebnisse Datenbereitstellung

.cols[
.fifty[
     
- Umfang (vorläufig):
  * 18 Bearbeiter, ~200 Emails
  * 16 Werke, 10 mit Double-Keying  
    → ` 6473` Seiten (vollständig)  
    → `  477` Seiten (vorausgewählt)  
    → `20808` Zeilen (vorausgewählt)  
    → `14909` Zeilen (korrigiert)  
    → `13335` Zeilen (übereinstnd.)
    
]

.fifty[
  
- Inter-Annotator-Agreement
    * 89% Zeilen (DK-Ausbeute)
    * **99.7%** Zeichen (= 0.3% CER)
- Genauigkeit Baseline-OCR
    * **97.2%** Zeichen (= 2.8% CER)
    * nur Fraktur
        * `GT4HistOCR+frk+Fraktur`
        * 98.8% Zeichen (= 1.2% CER)  
    * nur Antiqua
        * `deu+Latin`
        * 96.2% Zeichen (= 3.8% CER)  

]
]

---

class: part-slide

# Training

- Vorgehen
- Ergebnisse

---

# Training – Vorgehen

- Modelle für Tesseract  
  – mit [tesstrain](https://github.com/tesseract-ocr/tesstrain)
- randomisierte 10%-Aufteilung (Prüf- vs Lernstichprobe)  
  – je Werk
- Gruppierung der Dateipaare (werkspezifisch vs. generisch)  
  – per Symlinks
- Parameterwahl (Finetuning vs. Baseline)  
  – Basismodell, Lernrate und Iterationen
- Augmentierung (für robustere Modelle)  
  – Rauschen, Binarisierung, Drehung, Verzerrung

---

# Training – Ergebnisse

- werkspezifisches Finetuning
- generisches Finetuning (nur Fraktur)
- generisches Finetuning (nur Antiqua)
- generisches Finetuning (alles)
- generisches Baseline-Training (alles)
- generisches Baseline-Training (alles + GT4HistOCR)

| **Werk** | **CER vorher** | **CER nachher** |
| --- | --- | --- |
| `krankenkochbuch` | ?? | ?? |
| ... | ... | ... |
| gesamt | ?? | ?? |


---

class: part-slide

# Vielen Dank für Ihre Aufmerksamkeit!

.center[
[wrznr.github.io/bibliothekartag-2021](https://wrznr.github.io/bibliothekartag-2021)
[github.com/slub/slub_ocr_gt](https://github.com/slub/slub_ocr_gt)
]

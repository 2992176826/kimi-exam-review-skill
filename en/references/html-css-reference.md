# HTML/CSS Template Reference for Exam Review Materials

Reusable CSS and HTML structure for generating exam-focused review PDFs.

## HTML Structure Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>[Subject] - Exam Review</title>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Serif:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        /* CSS styles */
    </style>
</head>
<body>
    <div class="cover">
        <div class="cover-deco1"></div>
        <div class="cover-content">
            <div class="cover-tag">FINAL EXAM REVIEW</div>
            <div class="cover-title">[Subject] Exam Review</div>
            <div class="cover-subtitle">Based on past exam pattern analysis</div>
            <div class="cover-meta">
                Generated: [Date]<br>
                Textbook: [Version]<br>
                Papers covered: [Years]
            </div>
        </div>
    </div>

    <div class="toc-page">
        <div class="toc-title">Table of Contents</div>
        <ul class="toc">
            <li class="toc-l1"><a href="#sec1">1. Exam Pattern Overview</a></li>
            <li class="toc-l1"><a href="#sec2">2. Essay Templates by Chapter</a></li>
            <li class="toc-l1"><a href="#sec3">3. High-Frequency MCQs</a></li>
            <li class="toc-l1"><a href="#sec4">4. True/False Trap Collection</a></li>
            <li class="toc-l1"><a href="#sec5">5. Quick Comparison Tables</a></li>
            <li class="toc-l1"><a href="#sec6">6. Prediction Questions</a></li>
            <li class="toc-l1"><a href="#sec7">7. Last-Minute Review Card</a></li>
        </ul>
    </div>

    <h1 id="sec1">1. Exam Pattern Overview</h1>
    <div class="intro">...</div>

    <h1 id="sec2">2. Essay Templates by Chapter</h1>
    <div class="exam-template">...</div>

    <h1 id="sec3">3. High-Frequency MCQs</h1>
    <div class="choice-focus">...</div>
    <div class="keybox">...</div>

    <h1 id="sec4">4. True/False Trap Collection</h1>
    <div class="judge-trap">...</div>

    <h1 id="sec5">5. Quick Comparison Tables</h1>
    <table>...</table>

    <h1 id="sec6">6. Prediction Questions</h1>
    <div class="exam-template">...</div>

    <h1 id="sec7">7. Last-Minute Review Card</h1>
    <div class="mnemonic">...</div>
    <div class="quick-card">...</div>
</body>
</html>
```

## Complete CSS Stylesheet

```css
* { box-sizing: border-box; }

body {
    margin: 0; padding: 0;
    font-family: "Noto Serif", Georgia, serif;
    font-size: 10.5pt;
    line-height: 1.7;
    color: #333;
    text-align: justify;
    text-align-last: left;
    string-set: doctitle "";
}

@page {
    size: A4;
    margin: 2cm 1.8cm;
    @top-center { content: string(doctitle); font-size: 9pt; color: #666; }
    @bottom-center { content: counter(page); font-size: 9pt; color: #666; }
}
@page cover { @top-center { content: none; } @bottom-center { content: none; } }
@page toc { @top-center { content: none; } @bottom-center { content: none; } }

.cover { page: cover; }
.toc-page { page: toc; }

.cover {
    width: 210mm; height: 297mm;
    margin: 0; position: relative; overflow: hidden;
    page-break-after: always;
    background: linear-gradient(160deg, #faf8f3 0%, #f0ece0 40%, #e8e0cc 100%);
}
.cover::before {
    content: ""; position: absolute;
    top: -100px; right: -150px;
    width: 500px; height: 500px;
    border: 2px solid rgba(139,115,85,0.2); border-radius: 50%;
}
.cover::after {
    content: ""; position: absolute;
    bottom: -60px; left: -40px;
    width: 250px; height: 250px;
    border: 2px solid rgba(139,115,85,0.15); border-radius: 50%;
}
.cover-deco1 {
    position: absolute; top: 80px; left: 50px;
    width: 100px; height: 3px;
    background: linear-gradient(90deg, #8b7355, transparent);
}
.cover-content {
    position: absolute; top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    text-align: center; width: 80%; z-index: 1;
}
.cover-tag {
    font-size: 11pt; color: #8b7355;
    letter-spacing: 0.4em; margin-bottom: 2cm; font-weight: 600;
}
.cover-title {
    font-size: 24pt; font-weight: 700;
    color: #3a3228; margin-bottom: 0.6cm; line-height: 1.3;
}
.cover-subtitle {
    font-size: 13pt; color: #5a5248; margin-bottom: 3cm;
}
.cover-meta {
    font-size: 10pt; color: #666; line-height: 2;
}

.toc-page { page-break-after: always; padding-top: 0.5cm; }
.toc-title {
    font-size: 16pt; font-weight: 700; color: #333;
    text-align: center; margin-bottom: 1cm;
    padding-bottom: 0.3cm; border-bottom: 2px solid #8b7355;
}
.toc { list-style: none; padding: 0; margin: 0; }
.toc li { margin: 0.3em 0; }
.toc a { text-decoration: none; color: #333; display: flex; align-items: baseline; }
.toc a::after {
    content: leader('.') target-counter(attr(href url), page);
    flex: 1; text-align: right; margin-left: 0.5em;
}
.toc-l1 { font-weight: 700; font-size: 10.5pt; margin-top: 0.6em !important; }
.toc-l2 { padding-left: 1.5em; font-size: 10pt; }

h1 {
    font-size: 16pt; font-weight: 700; color: #3a3228;
    margin-top: 0; margin-bottom: 0.6cm;
    padding-bottom: 0.2cm; border-bottom: 2px solid #8b7355;
    string-set: doctitle content();
    page-break-before: always;
}
h1:first-of-type { page-break-before: auto; }

h2 {
    font-size: 13pt; font-weight: 700; color: #4a4238;
    margin-top: 1em; margin-bottom: 0.4em;
    padding-left: 0.4em; border-left: 4px solid #8b7355;
}

h3 {
    font-size: 11pt; font-weight: 600; color: #555;
    margin-top: 0.8em; margin-bottom: 0.3em;
}

.exam-template {
    background: #faf7f0;
    border: 1.5px solid #c9b896;
    padding: 0.8em 1em;
    margin: 0.8em 0;
    page-break-inside: avoid;
}
.exam-template-title {
    font-weight: 700; font-size: 10.5pt;
    color: #8b6914; margin-bottom: 0.4em;
    padding-bottom: 0.2em; border-bottom: 1px dashed #c9b896;
}
.exam-template ol { margin: 0.3em 0; padding-left: 1.5em; }
.exam-template li { margin: 0.2em 0; font-size: 9.5pt; }
.point-score {
    color: #b85c38; font-weight: 600; font-size: 9pt;
}

.keybox {
    background: #f5f0e8;
    border-left: 4px solid #8b7355;
    padding: 0.6em 0.8em;
    margin: 0.6em 0;
    page-break-inside: avoid;
}
.keybox-title {
    font-weight: 700; color: #8b5a2b;
    font-size: 10pt; margin-bottom: 0.2em;
}
.keybox ul { margin: 0.2em 0; padding-left: 1.5em; }
.keybox li { margin: 0.15em 0; font-size: 9.5pt; }

.choice-focus {
    background: #f0f5f0;
    border-left: 4px solid #5a8b5a;
    padding: 0.5em 0.8em;
    margin: 0.5em 0;
    page-break-inside: avoid;
}
.choice-focus-title {
    font-weight: 700; color: #3a6b3a;
    font-size: 9.5pt; margin-bottom: 0.2em;
}

.judge-trap {
    background: #f5f0f0;
    border-left: 4px solid #8b4a4a;
    padding: 0.5em 0.8em;
    margin: 0.5em 0;
    page-break-inside: avoid;
}
.judge-trap-title {
    font-weight: 700; color: #8b3a3a;
    font-size: 9.5pt; margin-bottom: 0.2em;
}

.intro {
    font-size: 10pt; color: #555; margin-bottom: 0.8em;
    padding: 0.4em 0.8em;
    background: #faf9f7; border-left: 3px solid #d4cfc0;
}

.mnemonic {
    background: #f8f5ee;
    border: 1px dashed #c9b896;
    padding: 0.5em 0.8em;
    margin: 0.6em 0;
    font-size: 9.5pt;
}
.mnemonic-title {
    font-weight: 700; color: #8b7355; margin-bottom: 0.3em;
}

.quick-card {
    background: #fff;
    border: 2px solid #8b7355;
    padding: 0.8em;
    margin: 0.6em 0;
    page-break-inside: avoid;
}
.quick-card-title {
    font-weight: 700; color: #3a3228;
    font-size: 11pt; margin-bottom: 0.4em;
    text-align: center;
    border-bottom: 1px solid #c9b896; padding-bottom: 0.3em;
}

.sp {
    background: #e8e0cc; padding: 0.05em 0.3em;
    font-size: 9pt; font-weight: 600; color: #4a4238;
}

.page-ref {
    color: #b85c38; font-size: 10pt; font-weight: 400;
}

table {
    width: 100%; max-width: 100%;
    border-collapse: collapse;
    margin: 0.6em 0; font-size: 9pt;
    page-break-inside: avoid;
}
caption {
    font-weight: 600; margin-bottom: 0.3em;
    text-align: center; color: #333; font-size: 9.5pt;
}
thead { display: table-header-group; }
thead tr { border-top: 1.5px solid #333; border-bottom: 1px solid #333; }
th { padding: 0.3em 0.4em; text-align: left; font-weight: 600;
     background: #f5f3ef; font-size: 9pt; }
td { padding: 0.25em 0.4em; text-align: left;
     vertical-align: top; font-size: 8.5pt; }
tbody tr { border-bottom: 0.5px solid #ddd; }
tbody tr:last-child { border-bottom: 1.5px solid #333; }
tr { page-break-inside: avoid; }

pre, table, figure, img, svg, blockquote {
    max-width: 100%; box-sizing: border-box;
}
a { word-break: break-all; color: #8b7355; }
ul, ol { margin: 0.3em 0; padding-left: 1.8em; }
li { margin: 0.15em 0; }
```

## Content Block Examples

### Essay Template
```html
<div class="exam-template">
    <div class="exam-template-title">Essay Template (10 pts) — [Topic]</div>
    <ol>
        <li><strong>Location and Scope</strong>: ... <span class="point-score">1 pt</span></li>
        <li><strong>Climate Characteristics</strong>: ... <span class="point-score">1 pt</span></li>
        <li><strong>Terrain Features</strong>: ... <span class="point-score">1 pt</span></li>
        <li><strong>Main Type A + Representative Species</strong>: ... <span class="point-score">1 pt</span></li>
        <li><strong>Main Type B + Representative Species</strong>: ... <span class="point-score">1 pt</span></li>
        <li><strong>Secondary/Degraded Ecosystems</strong>: ... <span class="point-score">1 pt</span></li>
        <li><strong>Rare/Endemic Species</strong>: ... <span class="point-score">1 pt</span></li>
        <li><strong>Economic Forest Species</strong>: ... <span class="point-score">1 pt</span></li>
        <li><strong>Afforestation/Restoration</strong>: ... <span class="point-score">1 pt</span></li>
        <li><strong>Introduced/Cultivated + Summary</strong>: ... <span class="point-score">1 pt</span></li>
    </ol>
</div>
```

### Last-Minute Review Card
```html
<div class="quick-card">
    <div class="quick-card-title">30-Minute Pre-Exam Review Card</div>
    <ul>
        <li><strong>Mnemonic</strong>: "Wei-Qi-Chui, Zhu-Ci-Geng, Jing-Yin-Te"</li>
        <li><strong>5 Must-Memorize Species</strong>: ... ... ... ... ...</li>
        <li><strong>3 Must-Know Formulas</strong>: ... ... ...</li>
    </ul>
</div>
```

### Mnemonic
```html
<div class="mnemonic">
    <div class="mnemonic-title">Memory Mnemonic</div>
    <strong>"Song-Shan-Bo, Nan-Luo"</strong><br>
    Pinaceae, Taxodiaceae, Cupressaceae, Araucariaceae, Podocarpaceae<br>
    <em>Features: Pines/firs needle/linear; cypress scale/needle alternate; Araucaria/Podocarp broad</em>
</div>
```

## Print to PDF

1. Save HTML as `.html` file
2. Open in Chrome/Edge
3. Ctrl+P → Destination: Save as PDF
4. More settings → Paper size: A4
5. Save

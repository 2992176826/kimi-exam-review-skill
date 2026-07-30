# HTML/CSS 打印模板参考

生成可打印的 A4 复习资料 PDF。

## HTML 结构模板

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>[科目] - 期末冲刺</title>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Serif+SC:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        /* CSS 样式 */
    </style>
</head>
<body>
    <div class="cover">
        <div class="cover-deco1"></div>
        <div class="cover-content">
            <div class="cover-tag">FINAL EXAM REVIEW</div>
            <div class="cover-title">[科目] 期末冲刺资料</div>
            <div class="cover-subtitle">基于历年真题模式分析</div>
            <div class="cover-meta">
                生成日期：2026年X月X日<br>
                教材版本：[版本]<br>
                覆盖试卷：[年份]
            </div>
        </div>
    </div>

    <div class="toc-page">
        <div class="toc-title">目 录</div>
        <ul class="toc">
            <li class="toc-l1"><a href="#sec1">一、考试模式概览</a></li>
            <li class="toc-l1"><a href="#sec2">二、各章论述题模板</a></li>
            <li class="toc-l1"><a href="#sec3">三、选择题高频考点</a></li>
            <li class="toc-l1"><a href="#sec4">四、判断改错陷阱集</a></li>
            <li class="toc-l1"><a href="#sec5">五、对比速记表</a></li>
            <li class="toc-l1"><a href="#sec6">六、押题预测</a></li>
            <li class="toc-l1"><a href="#sec7">七、考前速记卡</a></li>
        </ul>
    </div>

    <h1 id="sec1">一、考试模式概览</h1>
    <div class="intro">...</div>

    <h1 id="sec2">二、各章论述题模板</h1>
    <div class="exam-template">...</div>

    <h1 id="sec3">三、选择题高频考点</h1>
    <div class="choice-focus">...</div>
    <div class="keybox">...</div>

    <h1 id="sec4">四、判断改错陷阱集</h1>
    <div class="judge-trap">...</div>

    <h1 id="sec5">五、对比速记表</h1>
    <table>...</table>

    <h1 id="sec6">六、押题预测</h1>
    <div class="exam-template">...</div>

    <h1 id="sec7">七、考前速记卡</h1>
    <div class="mnemonic">...</div>
    <div class="quick-card">...</div>
</body>
</html>
```

## 完整 CSS 样式表

```css
* { box-sizing: border-box; }

body {
    margin: 0; padding: 0;
    font-family: "Noto Serif SC", Georgia, serif;
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

## 内容块示例

### 论述题模板
```html
<div class="exam-template">
    <div class="exam-template-title">论述题答题模板（10分）— [主题]</div>
    <ol>
        <li><strong>地理位置与范围</strong>：... <span class="point-score">1分</span></li>
        <li><strong>气候特征</strong>：... <span class="point-score">1分</span></li>
        <li><strong>地形地貌</strong>：... <span class="point-score">1分</span></li>
        <li><strong>主要类型 A + 代表种</strong>：... <span class="point-score">1分</span></li>
        <li><strong>主要类型 B + 代表种</strong>：... <span class="point-score">1分</span></li>
        <li><strong>次生植被/退化生态系统</strong>：... <span class="point-score">1分</span></li>
        <li><strong>珍稀/特有物种</strong>：... <span class="point-score">1分</span></li>
        <li><strong>经济林树种</strong>：... <span class="point-score">1分</span></li>
        <li><strong>造林/恢复树种</strong>：... <span class="point-score">1分</span></li>
        <li><strong>引种/栽培种 + 总结</strong>：... <span class="point-score">1分</span></li>
    </ol>
</div>
```

### 考前速记卡
```html
<div class="quick-card">
    <div class="quick-card-title">考前 30 分钟速记卡</div>
    <ul>
        <li><strong>口诀</strong>："位气垂，主次更，经引特"</li>
        <li><strong>必背 5 个种</strong>：... ... ... ... ...</li>
        <li><strong>必背 3 个公式</strong>：... ... ...</li>
    </ul>
</div>
```

### 记忆口诀
```html
<div class="mnemonic">
    <div class="mnemonic-title">记忆口诀</div>
    <strong>"松杉柏，南罗"</strong><br>
    松科、杉科、柏科、南洋杉科、罗汉松科<br>
    <em>特征：松杉叶针条形，柏鳞刺交互，南洋罗汉叶宽</em>
</div>
```

## 打印为 PDF

1. 保存 HTML 为 `.html` 文件
2. 用 Chrome/Edge 打开
3. Ctrl+P → 目标：另存为 PDF
4. 更多设置 → 纸张尺寸：A4
5. 保存

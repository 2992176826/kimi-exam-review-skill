# 🎓 Kimi 通用考试复习 Skill

面向全球用户的 AI 考试复习智能体技能，支持中英双语输入。

## 核心能力

| 能力 | 说明 |
|------|------|
| 试卷模式逆向工程 | 分析历年真题，拆解每种题型的得分维度 |
| 跨学科自适应 | STEM / 文科 / 医学 / 编程 自动切换框架 |
| 记忆科学整合 | 间隔重复、主动回忆、费曼技巧、记忆宫殿 |
| 多格式输出 | HTML 打印 PDF / Anki 卡片 / Markdown 笔记 / JSON 题库 |
| 押题预测 | 补洞法、邻接法、周年法、前沿法、对称法 |
| 中英双语 | 自动识别用户语言，中文/英文无缝切换 |

## 仓库结构

- `README.md` — 本文件（中文说明）
- `SKILL.md` — 通用入口（自动识别语言并路由）
- `zh/` — 中文技能包
  - `SKILL.md`
  - `references/`
    - `exam-patterns.md`
    - `memory-science.md`
    - `cross-subject-adaptation.md`
    - `html-css-reference.md`
- `en/` — English Skill Pack
  - `SKILL.md`
  - `references/`
    - `exam-patterns.md`
    - `memory-science.md`
    - `cross-subject-adaptation.md`
    - `html-css-reference.md`

## 触发词（中英双语）

中文："整理复习资料"、"生成复习材料"、"帮我考研"、"刷题"、"错题整理"、"anki"、"背书"、"冲刺"、"押题"

English: "create review notes", "prepare for exam", "study guide", "flashcards", "quiz me", "mock exam", "error log", "final review"

## 使用方法

### 方式 1：直接对话（推荐）
上传教材 + 试卷，说："整理树木分类学期末复习资料，输出打印 PDF"

或英文：Upload textbook + past papers, say: "Create a dendrology final exam review, output printable PDF"

### 方式 2：跨会话复用
1. 打开本 GitHub 仓库
2. 复制 `SKILL.md` 内容 → 粘贴到 Kimi 作为「常用语」
3. 或发送仓库链接，说："按这个 skill 的流程，生成 [科目] 复习资料"

### 方式 3：指定语言
- 中文用户：Kimi 自动调用 `zh/` 目录下的技能文件
- English users: Kimi automatically loads skill files from `en/` directory

## 通用口诀

论述题得分维度（跨学科通用）：

> **"位气垂，主次更，经引特"**
> 
> 位(位置) → 气(气候/背景) → 垂(结构/分布) → 主(主要类型) → 次(次要类型) → 更(管理/更新) → 经(经济价值) → 引(引种/应用) → 特(特殊/特有)

## 输出格式

| 格式 | 适用场景 | 操作 |
|------|----------|------|
| HTML | 打印纸质复习资料 | 浏览器打开 → 打印为 PDF |
| Anki CSV | 记忆卡片 | 导入 Anki/Quizlet |
| Markdown | 数字笔记 | 粘贴到 Obsidian/Notion |
| JSON | 自建题库 | 导入刷题软件 |

## 作者

yanhaotian@njfu.edu.cn

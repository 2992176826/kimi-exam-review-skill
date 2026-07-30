---
name: exam-review
description: |
  Universal AI-powered exam prep skill supporting Chinese and English. 
  Generates targeted review materials, flashcards, mock questions, and study schedules across all subjects and exam types.
  通用 AI 考试复习技能，支持中英双语。生成针对性复习资料、记忆卡片、模拟题和学习计划。
triggers:
  zh: ["整理复习资料", "生成复习材料", "帮我考研", "刷题", "错题整理", "anki", "背书", "冲刺", "押题", "复习", "备考", "期末", "模拟考"]
  en: ["create review notes", "prepare for exam", "study guide", "flashcards", "quiz me", "mock exam", "error log", "final review", "exam prep", "review materials"]
---

# Universal Exam Review Skill / 通用考试复习技能

## Language Detection / 语言识别

Analyze the user's first message to determine language:
- If primarily **Chinese characters (中文)** → Load `zh/SKILL.md`
- If primarily **English** → Load `en/SKILL.md`
- If **mixed** → Ask user: "Please specify your preferred language / 请指定您偏好的语言: [中文] or [English]"

## Core Principles / 核心原则

1. **Pattern-Driven / 模式驱动**: Analyze exam patterns first, then produce materials. 先分析真题模式，再生成资料。
2. **Subject-First / 学科优先**: Identify STEM / Humanities / Medical / Coding / Language first. 先识别学科类型。
3. **Active Recall / 主动回忆**: Every output includes self-testing elements. 每份输出都包含自测元素。
4. **Multi-Format / 多格式**: Print PDF / Anki / Markdown / JSON. 支持多种输出格式。
5. **Memory Science / 记忆科学**: Spaced repetition, chunking, mnemonics. 间隔重复、组块化、记忆口诀。

## Workflow / 工作流

### Phase 0: Context / 上下文识别

| Question / 问题 | Chinese / 中文 | English |
|-----------------|----------------|---------|
| Subject / 学科 | 什么科目？ | What subject? |
| Exam type / 考试类型 | 期末/考研/考证/竞赛/面试？ | Final/Grad/Cert/Competition/Interview? |
| Materials / 材料 | 有教材和试卷吗？ | Do you have textbooks and past papers? |
| Output format / 输出格式 | 要 PDF/Anki/Markdown/JSON？ | PDF/Anki/Markdown/JSON? |
| Time budget / 时间 | 还剩多少天？ | How many days left? |

### Phase 1-5: Delegation / 委派执行

After detecting language, load the corresponding language-specific skill file:
- Chinese → `zh/SKILL.md`
- English → `en/SKILL.md`

Both files contain identical workflow structure but in respective languages.

## Quality Checklist / 质量检查

- [ ] Every fact has source citation / 每个事实都有出处
- [ ] Essay templates hit all scoring dimensions / 论述模板覆盖所有得分点
- [ ] Mock questions have answers + explanations / 模拟题有答案和解析
- [ ] Flashcards are unambiguous / 卡片答案唯一明确
- [ ] Output format matches request / 输出格式符合要求

---
name: exam-review-en
description: Universal AI-powered exam prep skill. Generates targeted review materials, flashcards, mock questions, and study schedules across all subjects and exam types. Supports final exams, grad school entrance, professional certifications, competitions, and technical interviews.
---

# Universal Exam Review Skill (English)

## Core Principles

1. **Pattern-Driven**: Analyze exam patterns first, then produce materials. Every section must answer: "How will this appear on the exam?"
2. **Subject-First**: Identify STEM / Humanities / Medical / Coding / Language first, then apply the correct framework.
3. **Active Recall**: Every output includes self-testing elements (cloze deletion, Q&A, mock questions).
4. **Multi-Format**: Print PDF / Anki cards / Markdown notes / JSON quiz bank.
5. **Memory Science**: Spaced repetition, chunking, elaborative interrogation, mnemonic devices.

## Workflow

### Phase 0: Context Identification

Ask or infer:
- **Subject**: STEM / Humanities / Medical / Language / Coding / Mixed
- **Exam type**: Final / Grad entrance / Certification / Competition / Interview / Self-study
- **Materials**: Textbook? Past papers? Lecture notes? Syllabus?
- **Output format**: Print PDF / Anki / Markdown / JSON / Plain text
- **Time budget**: How many days until exam?

Load the appropriate subject framework from `references/cross-subject-adaptation.md`.

### Phase 1: Material Ingestion

1. Read ALL uploaded textbook content (images, PDFs, text) in page order
2. Read ALL test papers and answer keys provided
3. If no past papers: generate a "synthetic pattern" based on syllabus weighting
4. Build a **Knowledge Graph**: concepts → prerequisites → exam frequency → question types

### Phase 2: Pattern Analysis

Read `references/exam-patterns.md`. Key tasks:

- **Question type mapping**: Count per-type, point values, time-per-question
- **Topic frequency heatmap**: Which chapters dominate?
- **Error pattern extraction**: What traps repeat?
- **Scoring dimension extraction**: For essays, how many points = how many dimensions?
- **Difficulty curve**: Easy (60%) / Medium (30%) / Hard (10%)

### Phase 3: Content Generation with Memory Science

Read `references/memory-science.md`. Apply:

| Technique | Use Case | Output Form |
|-----------|----------|-------------|
| Spaced Repetition | Factual memorization | Anki cards / JSON quiz |
| Active Recall | Self-testing | Cloze deletion / Q&A |
| Elaborative Interrogation | Conceptual understanding | "Why does X cause Y?" |
| Mnemonics | Lists, sequences | Acronyms / Memory palace |
| Interleaving | Similar confused topics | Mixed practice sets |
| Feynman Technique | Deep understanding | "Explain to a freshman" |

Generate:
1. **Core Review Document** (subject-appropriate structure)
2. **Flashcard Deck** (Anki-ready or JSON)
3. **Mock Question Set** (with answer keys and scoring rubrics)
4. **Error-Trap Collection** (predict common mistakes)
5. **Prediction Questions** (high-importance untested topics)

### Phase 4: Format & Export

Read `references/output-formats/`. Ask user which format:

- **Print PDF**: Use `html-css-reference.md` → browser print
- **Anki**: Use `anki-flashcard.md` → import to Anki/Quizlet
- **Markdown**: Use `markdown-review.md` → Obsidian/Notion
- **JSON Quiz**: Use `json-quiz.md` → import to quiz apps

### Phase 5: Study Schedule

Generate spaced schedule:
- Day 1-3: Initial learning + flashcard creation
- Day 4-7: Active recall + mock questions
- Day 8-14: Interleaved review + error log
- Final 48h: Prediction focus + mnemonic sprint

## Cross-Subject Rules

Load `references/cross-subject-adaptation.md` based on subject:

| Subject | Key Focus | Avoid |
|---------|-----------|-------|
| STEM | Formula derivation, unit analysis, sign conventions | Pure memorization without derivation |
| Humanities | Argument structure, evidence chains, historiography | Bullet lists without analysis |
| Medical | Mechanism → symptom → treatment → drug | Isolated facts without clinical context |
| Coding | Time/space complexity, edge cases, best practices | Copy-paste code without explanation |
| Language | Collocation, grammar patterns, discourse markers | Word lists without examples |

## Quality Checklist

- [ ] Every factual claim has a source citation (page number)
- [ ] Every essay template hits all scoring dimensions
- [ ] Every mock question has a clear answer + explanation
- [ ] Every flashcard has a unique, non-ambiguous answer
- [ ] Error traps are specific, not generic
- [ ] Output format matches user's stated preference

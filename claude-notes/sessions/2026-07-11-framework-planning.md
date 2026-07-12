# Session: 2026-07-11 framework planning review

Purpose: full review of repo framework before first syllabus generation. User asked for
one-question-at-a-time planning dialog. Shared findings live in /plan-assessment.md
(sections A/B/C, question queue at bottom) — that doc + this file = resume point.

## State

- Repo reviewed in full: README, 6 skills, 5 templates, empty syllabus.md + vocab.md.
- plan-assessment.md created with findings A1–A3, B1–B5, C1–C8 and question queue.
- Today is Saturday of WEEK 0 (week of 2026-07-06). No lessons exist yet. First real
  syllabus generation presumably targets WEEK 1 (starting Mon 2026-07-13) — confirm
  during the timing/bootstrap question.

## Q&A log

- Q1 (A1, lesson dir naming): ANSWERED — week-based `lesson-w<nn>-<m>` zero-padded
  (lesson-w03-2). Fixes applied to README x3, lesson-notes.template, syllabus.template,
  life-happens skill. A1 closed.
- Q2 (B2, starting level / bootstrap): ANSWERED — rusty school Latin. learner-model.md
  founded with baseline; plan-syllabus got a First-Run Bootstrap section (placement
  diagnostic via graded sentences). B2 closed.
- Q3 (C1, mid-block adaptivity): ANSWERED (user clarified in chat, rejected my option
  list — his own design was better). Decisions: (a) first block = beginner-calibrated
  SPEED RUN, expect poorest fit, under-shoot difficulty; (b) new not-working skill created
  as the mid-block ejection seat (diagnose one-question-at-a-time → roll up partial
  progress → trigger plan-syllabus). I added a vocab-reconciliation rule to it (append-only
  vocab.md means ejected weeks' unstudied words get carried forward or explicitly
  superseded in the re-plan's Planning Notes, never silently duplicated) and a
  delete-unstarted-materials-with-tombstone rule — FLAG BOTH to user in next summary,
  they're my judgment calls inside his skill.
- Q4 (C2, model/effort conventions): ANSWERED & CLOSED — keep README as written (Opus
  plans / Sonnet executes); Sonnata→Sonnet fixed. Docs verification (claude-code-guide
  agent) confirmed: README/CLAUDE.md prose CANNOT override CLI model selection (his
  condition satisfied); SKILL.md `model:` frontmatter exists but only lasts one turn →
  useless for his multi-turn sessions; manual /model stays the mechanism. FALLOUT: all 7
  skills had invalid `disallow-model-invocation` (real field: `disable-model-invocation`,
  silently ignored until now) + fake tools WebEdit/WebGet (→WebFetch). All fixed.
  `version:` frontmatter and `LS` tool are unsupported-but-inert; left in place.

## Session resumed (2026-07-11, later)

- Q5 (B3, transcript.md): ANSWERED — DROP transcript.md entirely (he chose against my
  distilled-record rec; he won't re-read them). README lesson-folder list updated;
  teach-lesson gained "Closing the Lesson" section (Evaluation Notes + claude-notes
  update are now mandatory end-of-lesson duties). B3 closed.
- Q6 (C5, Anki export): ANSWERED — NO export, ever. Hand-typing cards is his deliberate
  first encoding pass. Recorded in learner-model. C5 closed as intentional friction.
- Q7 (C6, lesson duration): ANSWERED — ~30 min target, one concept per lesson, flex only
  when struggling. ~9 hrs/week all-in. README + teach-lesson + learner-model updated.
- Q8 (batch): APPROVED ALL SEVEN, applied: (1) .claude/SKILLS→skills + claude.md→CLAUDE.md
  via two-step git mv; (2) ./readings/ created; (3) grade-homework now writes lesson-notes
  ## Homework Evaluation summary (detail stays in homework.md ## Evaluation); (4) templates
  line added to README structure list; (5) reading filenames now reading-w<nn>-<id>-<desc>.md;
  (6) Providence→Provenance in README + template (+umabiguous typo); (7) plan-syllabus must
  WebSearch-verify historical attributions at planning time.

## SESSION COMPLETE (2026-07-11)

All findings A1–A3, B1–B5, C1–C8 resolved. plan-assessment.md is the full record.
Framework is ready. NEXT REAL ACTION: user commits, then invokes plan-syllabus →
First-Run Bootstrap → placement diagnostic → first 4-week block as beginner-calibrated
SPEED RUN (his directive). Deliberately left open: vocab-and-grammar.md has no template
(freeform per-lesson reference; add template only if shape drifts).
Working-style note saved to persistent memory: one question at a time + recommendation;
he counter-designs (ejection-seat skill was his); never offer Anki exports.

## Things I noticed but haven't queued as questions (judgment calls, mention if relevant)

- README line 9-10 "Sonnata" = Sonnet, almost certainly. Folded into C2 (models question).
- sitrep skill says "CERF" for CEFR — cosmetic, fix in the batch pass.
- User's stated stance: Cicero-inspired, respects but doesn't want Caesar's viewpoint to
  dominate reading selection. Important for future reading/vocab curation — move this into
  learner-model.md when created.
- Vocab: frequency-weighted selection is CRITICAL to user ("ground speed toward fluency").
- Style: no macrons / no vocab handles / no annotations in readings + homework; macrons OK
  in vocab lists and lessons. "Ergonomic assist" features are for lessons only.

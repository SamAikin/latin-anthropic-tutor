# Plan Assessment — Framework Review & Planning Session

Started: 2026-07-11 (Saturday of WEEK 0). This document tracks the full review of the repo
framework and the decisions we make during planning sessions. If we stop mid-chat, this doc
plus ./claude-notes/ is the resume point.

## Overall Read

The framework is coherent and well-conceived. The strongest parts:

- Clear separation of concerns: shared-contract files (syllabus.md, vocab.md, lesson folders)
  vs. model-private state (./claude-notes/).
- Append-only vocab.md + git-history-as-archive for syllabus.md is a clean pattern.
- The skill set maps 1:1 onto the real workflow stages (plan → teach → homework → reading →
  adjust → report).
- The 4-week "don't build railroad tracks too far out" planning horizon with gradient
  recalculation is the right adaptive loop.

Below are the findings, grouped by severity. Question numbers (Q1, Q2, ...) track what we
discuss in-chat, one at a time. Status: ⬜ open · 🔶 in discussion · ✅ resolved.

## A. Direct Collisions (contradictions in the docs)

### A1. Lesson directory naming — two incompatible conventions ✅ (Q1)

- README "LESSONS" section (line 32) and the life-happens skill: `lesson-<weekn>-<m>`
- README "Repo Structure" (line 53), lesson-notes.template header, and syllabus.template
  (line 10): `lesson-<YYYYMMDD>` / `./lessons/lesson-20260701/`

These cannot both be the convention. Everything else in the system (vocab weeks, reading
filenames, syllabus sections, WEEK 0 anchor) is organized by week number, and life-happens
explicitly renames `lesson-<weekn>-<m>` folders — so week-based appears to be the newer
intent, with the date-based references being leftovers.

**DECIDED (Q1):** week-based, zero-padded: `lesson-w<nn>-<m>` (e.g. `lesson-w03-2`).
Fixes applied to README (3 spots), lesson-notes.template header, syllabus.template, and
life-happens skill for uniform notation.

### A2. `.claude/SKILLS/` casing + `.claude/claude.md` naming ✅ (Q8)

Claude Code's conventions are `.claude/skills/` (lowercase) and `.claude/CLAUDE.md`; the old
casing only worked because macOS is case-insensitive. **Fixed:** renamed via two-step git mv
(git tracked both as clean renames).

### A3. Tool-name and frontmatter typos in skills ✅ (fixed 2026-07-11)

- plan-syllabus `allowed-tools` listed `WebEdit`; teach-lesson and sitrep listed `WebGet` —
  neither is a real tool. All corrected to `WebFetch`.
- Verified against official docs (code.claude.com/docs/en/skills): the real field is
  `disable-model-invocation`. Every skill was using `disallow-model-invocation` (sitrep a
  third variant) — **silently ignored**, so nothing was actually preventing auto-invocation.
  Fixed in all 7 skills.
- Noted but left alone (harmless/inert): `version:` is not an officially supported
  frontmatter field (ignored), and `LS` is a legacy tool name.

## B. Missing Pieces (referenced but not present / no owner)

### B1. `./readings/` directory doesn't exist ✅ (Q8)

**Fixed:** created with .gitkeep.

### B2. No bootstrap / onboarding path for the *first* syllabus ✅ (Q2)

plan-syllabus assumed an existing syllabus.md and lesson-notes history; neither exists yet,
and nothing established the learner's starting level.

**DECIDED (Q2):** Starting level is **rusty school Latin** (studied years ago, expects
concepts to resurface with review) — recorded as the founding entry of the learner model in
./claude-notes/. plan-syllabus now has a "First-Run Bootstrap" section: when there is no
history, run a short in-chat placement diagnostic (graded sentences, ramping difficulty)
rather than relying on self-report, and calibrate the first block from the results.

### B3. teach-lesson has no end-of-lesson duties ✅ (Q5)

lesson-notes.template's `## Evaluation Notes` says it's "completed by you as we finish the
lesson," and README said each lesson folder contains `transcript.md` — but the teach-lesson
skill never instructed either.

**DECIDED (Q5):** transcript.md is **dropped** — Evaluation Notes carry the planning state,
homework tests retention, and the artifact would add end-of-lesson overhead without being
re-read. Removed from README's lesson-folder list. teach-lesson gained a "Closing the
Lesson" section: write clean `## Evaluation Notes` + update claude-notes before the session
ends.

### B4. grade-homework doesn't close the loop to lesson-notes.md ✅ (Q8, merged with C7)

**Fixed:** grade-homework now instructs updating the lesson's lesson-notes.md `## Homework
Evaluation`, and codifies the division: detailed corrections in homework.md `## Evaluation`,
higher-level summary for planning in lesson-notes.md.

### B5. README's repo-structure list omits ./templates/ ✅ (Q8)

**Fixed:** ./templates/ line added to the Repo Structure list.

## C. Fuzzy Edges (design tensions worth a decision)

### C1. Mid-block adaptivity vs. pre-generated materials ✅ (Q3)

Each planning session pre-generates ~16 lesson folders, ~24 readings, ~280 vocab words. If
week 1 of a block reveals a struggle, weeks 2–4 are already baked; the gradient only
recalculates every 4 weeks. life-happens handles *schedule* changes, not *content* changes.

**DECIDED (Q3):** Two-part answer.
1. *First block:* calibrate as if for a beginner and let the learner speed-run it —
   under-shooting difficulty at a brisk pace is the cheaper miss. Wired into plan-syllabus's
   First-Run Bootstrap section. After block one, the 4-week cycle is expected to self-correct.
2. *Ejection seat:* new skill `.claude/SKILLS/not-working/SKILL.md` for genuine mid-block
   non-fit (too hard, or far too easy), typically detected 1–2 weeks in. It diagnoses via
   one-question-at-a-time, rolls up partial progress (closing lesson notes, syllabus
   Adjustments tombstone, deletes unstarted materials, reconciles unstudied vocab), then
   triggers plan-syllabus for a fresh block. Distinct from life-happens (schedule vs fit).

### C2. Model references are dated ✅ (Q4)

README says "Opus 4.x" for planning and "Sonnata" (Sonnet?) for lessons.

**DECIDED (Q4):** Keep the convention as written (Opus plans / Sonnet executes); "Sonnata"
typo fixed to "Sonnet". User's condition — that repo docs cannot silently override his
manual CLI model choice — was verified against official docs: README/CLAUDE.md prose has
no model-selection power; only /model, --model, ANTHROPIC_DEFAULT_MODEL, or settings.json
do. SKILL.md does support a `model:` frontmatter override, but it lasts only one turn, so
it's useless for multi-turn planning/lesson sessions — manual /model remains the
enforcement mechanism, backed by plan-syllabus's "confirm the model with me" line.

### C3. Reading filename doesn't sort chronologically ✅ (Q8)

**Fixed:** convention is now `reading-w<nn>-<id#>-<desc>.md`
(e.g. reading-w03-2-cicero-in-catilinam.md); README updated.

### C4. "Providence" → "Provenance" ✅ (Q8)

**Fixed** in README and daily-reading.template (section header is now "## Provenance and
Citations"); also fixed "umabiguous" typo in the same template paragraph.

### C5. Anki hand-off friction ✅ (Q6)

vocab.md's format is human-readable but not Anki-importable; 70 words/week means real manual
entry effort.

**DECIDED (Q6):** No export artifact — hand-entering cards is a deliberate first encoding
pass and stays. C5 closes as *intentional friction*; no repo changes.

### C6. Weekly time budget — sanity check ✅ (Q7)

4 lessons (length was unspecified) + 4 homework (15–45 min) + 6 readings (~30 min) + daily
Anki (10 new words/day) ≈ 7 hrs/week before lessons.

**DECIDED (Q7):** Lessons target **~30 minutes** each — tight, generally one concept per
lesson, flexing longer only when a struggle warrants. All-in weekly commitment ≈ 9 hrs.
Recorded in README (LESSONS section), teach-lesson skill, and learner model.

### C7. Homework evaluation lives in two places — confirm the division ✅ (Q8)

Confirmed intentional and now codified in grade-homework (see B4).

### C8. Historical-provenance verification ✅ (Q8)

**Fixed:** plan-syllabus workflow now requires WebSearch verification of attribution and
wording for any reading presented as historical (or reworked historical) text.

## Decision Log

| # | Question | Decision | Date |
|---|----------|----------|------|
| Q1 | Lesson dir naming (A1) | ✅ `lesson-w<nn>-<m>`, zero-padded (e.g. lesson-w03-2). Stale date-based refs fixed. | 2026-07-11 |
| Q2 | Starting level / bootstrap (B2) | ✅ Rusty school Latin; bootstrap + placement diagnostic added to plan-syllabus. | 2026-07-11 |
| Q3 | Mid-block adaptivity (C1) | ✅ First block: beginner-calibrated speed run. New not-working skill = mid-block ejection seat → re-plan. | 2026-07-11 |
| Q4 | Model + effort conventions (C2) | ✅ Keep as written (Opus plans / Sonnet executes); verified docs can't override CLI model choice; Sonnata→Sonnet fixed. | 2026-07-11 |
| — | Skill frontmatter bugs (A3) | ✅ Fixed all 7 skills: disable-model-invocation spelling, WebFetch tool names. | 2026-07-11 |
| Q5 | transcript.md (B3) | ✅ Dropped. teach-lesson gained Closing-the-Lesson duties (Evaluation Notes + claude-notes). | 2026-07-11 |
| Q6 | Anki export (C5) | ✅ None — hand-entry kept as deliberate first study pass. | 2026-07-11 |
| Q7 | Lesson duration (C6) | ✅ ~30 min target, one concept/lesson; ~9 hrs/week all-in. | 2026-07-11 |
| Q8 | Small-fix batch | ✅ All seven applied: skills/ + CLAUDE.md renames, readings/ dir, grade-homework loop, templates in README, reading filename order, Provenance fix, WebSearch provenance verification. | 2026-07-11 |

## Question Queue (rough order; one at a time in chat)

1. ~~Q1: Lesson folder naming convention (A1)~~ ✅
2. ~~Q2: Starting level / placement for first syllabus (B2)~~ ✅
3. ~~Q3: Mid-block adaptivity trade-off (C1)~~ ✅ (speed-run first block + not-working skill)
4. ~~Q4: Model + effort conventions update (C2)~~ ✅ (keep as written; A3 frontmatter bugs fixed as fallout)
5. ~~Q5: transcript.md (B3)~~ ✅ (dropped; teach-lesson closing duties added)
6. ~~Q6: Anki export format (C5)~~ ✅ (none — intentional friction)
7. ~~Q7: Time budget / lesson duration (C6)~~ ✅ (~30 min lessons)
8. ~~Q8: Batch of small fixes~~ ✅ (all seven applied)

## SESSION COMPLETE (2026-07-11)

All findings resolved (A1–A3, B1–B5, C1–C8). The framework review is done.

**Next step:** commit, then invoke the plan-syllabus skill to generate the first 4-week
block. It will run the placement diagnostic (First-Run Bootstrap), and the block is
calibrated as a beginner-level speed run per Q3.

One observation left deliberately open (no action needed): lesson folders include a
vocab-and-grammar.md, which has no template — treated as freeform per-lesson reference
material generated from the lesson plan. Add a template later only if its shape starts
drifting.

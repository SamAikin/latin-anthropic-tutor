# compress-notes skill — BUILT 2026-07-15 (`.claude/skills/compress-notes/SKILL.md`)

Design record kept for the *why* behind the skill's rules. plan-syllabus workflow now
invokes the compression procedure as its first step.

Co-designed via feynman dialogue; all decisions below user-approved. Folded in from
the (deleted) handoff-organization.md after the 00-index refactor completed 2026-07-15.
All open questions resolved 2026-07-15 — see final section. Design is build-ready.

## Ratified decisions

- **Distill-and-archive, never destructive.** Mirrors context compaction faithfully:
  regenerate a compact working file, move raw dated entries to `claude-notes/archive/`
  (greppable; a bad distillation is recoverable). Archive reads expected to be rare
  (few per block) *if* distilled signals carry their residue inline.
- **Distillation = exponential smoothing.** The skill produces a longitudinal analysis
  of signal, not a summary: recent evidence dominates; signal from 3 weeks ago weighs
  much less than this week's. Each distilled signal keeps **count + last-confirmed
  date + one exemplar** (e.g. "idiom-inference: confirmed strength, 4 instances, last
  2026-07-14, e.g. odio habent→hate untaught").
- **Watch-items decay by OPPORTUNITY, not calendar.** "No traps encountered in 3
  readings" must not smooth toward closure. This is why the syllabus is an input:
  it says whether the coming block even presents the opportunity — flag "untested,
  not resolved."
- **Two species of content.** Signals/evidence → smooth + archive. Baseline/directives/
  taste ("never generate card exports", "no macrons in readings", Cicero-vista
  curation) → carry forward VERBATIM, never smoothed; a week-1 directive binds at
  full weight in week 30. (User expects Baseline growth to plateau now that the
  working agreement is established.)
- **Triggers:** (a) the syllabus-planning cycle — runs just before plan-syllabus;
  its distilled output doubles as the syllabus-planning brief; (b) **manual** — user
  invokes when he notices me struggling to work with state and still make good
  decisions. (Size backstop ~500 lines mid-block was recommended; not explicitly
  ratified.)
- **Scope: whole claude-notes/ space, per-file policy:**
  | file | policy |
  |---|---|
  | learner-model.md Signals | smooth + archive raw entries |
  | learner-model.md Baseline | verbatim carry-forward |
  | week-log.md | EXEMPT — it is data (a table), not signal; lossy compaction destroys it |
  | sessions/ | archive wholesale anything older than the current block |
  | 00-index.md | stays a pure map |
  | conventions.md | operating rules — stay full-strength |
  | lessons-learned.md | rules stay full-strength; incident narratives may archive once distilled |
- **Inputs: notes + syllabus ONLY — not lesson materials.** Signals already are the
  graded residue of the materials; a heavy skill defeats the manual "Claude is
  struggling" use case.

## Open questions — ALL RESOLVED 2026-07-15

- **Archive layout** (my call, per user's standing deference on space structure):
  `claude-notes/archive/`, one dated file per compress run per source, e.g.
  `archive/2026-08-09-learner-model-signals.md` — each run's raw material stays
  greppable as a unit.
- **Verification** (user-ratified): **no approval gate — invariant self-checks plus a
  compact report.** Hard invariants checked mechanically: every raw dated entry lands
  verbatim in archive; Baseline diff is zero; week-log untouched; every distilled
  signal carries count + last-confirmed date + exemplar residue. Then a short
  after-action report in chat (what smoothed, what archived, line counts before/after).
  Rationale: archive + git make a malignant compression recoverable, so a gate buys
  little; user explicitly accepted rollback-from-archive as the safety net.
- **Packaging** (answered from files): `.claude/skills/compress-notes/SKILL.md`
  alongside the other six project skills. Set `disable-model-invocation: true` —
  both ratified triggers are explicit (planning cycle, manual); self-triggered
  compression was never ratified.
- **plan-syllabus co-design** (answered from files): plan-syllabus has no structured
  input format — its step 1 is "read the claude-notes space," so a freshly distilled
  space IS the planning brief. No separate brief artifact (duplicate signal would
  drift). Integration = one-line addition to plan-syllabus's workflow: run
  compress-notes before reading the space.

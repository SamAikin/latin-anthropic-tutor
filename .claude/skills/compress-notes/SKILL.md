---
name: compress-notes
description: Distill-and-archive compression of the ./claude-notes/ stateful space — the written-notes analog of context-window compaction. Runs at the start of every syllabus-planning cycle, or manually when the user notices Claude struggling to use its state well.
version: 1.0.0
allowed-tools: Read, Write, Edit, Grep, Glob, LS
disable-model-invocation: true
---

# compress-notes

The ./claude-notes/ space grows append-only between planning blocks. Left alone, old
raw entries get read at equal weight with new ones and become anti-signal (a since-fixed
tense slip reads like a live problem). This skill regenerates the space as a compact
longitudinal analysis and moves the raw material to a greppable archive. It is
**distill-and-archive, never destructive**: a bad distillation is always recoverable
from `claude-notes/archive/` and git.

Both triggers are explicit — this skill must never self-trigger:
1. **Planning cycle**: plan-syllabus runs this procedure before reading the space; the
   freshly distilled space IS the planning brief (plan-syllabus has no separate input
   format — its first step is "read the space").
2. **Manual**: the user invokes `/compress-notes` when he notices me struggling to work
   with state and still make good decisions.

## Inputs

Read ONLY `./claude-notes/` and `./syllabus.md`. Do NOT read lesson materials — the
Signals entries already are the graded residue of those materials, and a heavy skill
defeats the manual "Claude is struggling" trigger.

The syllabus is an input for one specific reason: **watch-items decay by OPPORTUNITY,
not calendar.** "No traps encountered in 3 readings" must not smooth toward closure if
those readings never presented the trap. Check the coming block: if it doesn't present
the opportunity, mark the item "untested, not resolved" — never closed.

## The distillation operator

Distillation = **exponential smoothing**, not summarization. Recent evidence dominates;
signal from 3 weeks ago weighs much less than this week's. The output is a longitudinal
analysis of where each signal STANDS NOW, not a digest of what happened.

There are **two species of content — never confuse them**:

- **Signals/evidence** (dated entries, graded observations, watch-items): smooth into
  the distilled model; move the raw entries to archive. Every distilled signal MUST
  carry its residue inline: **count + last-confirmed date + one exemplar**, e.g.
  `idiom-inference: confirmed strength, 4 instances, last 2026-07-14, e.g. odio
  habent→hate untaught`. The residue is what keeps archive reads rare; without it,
  every claim becomes unfalsifiable dogma.
- **Baseline/directives/taste** ("never generate card exports", "no macrons in
  readings", the Cicero-vista curation): carry forward **VERBATIM, never smoothed**.
  A week-1 directive binds at full weight in week 30.

## Per-file policy

| file | policy |
|---|---|
| `learner-model.md` § Baseline | verbatim carry-forward — zero diff |
| `learner-model.md` § Signals | smooth + archive the raw dated entries |
| `learner-model.md` § Vocab tracking | word registries (assigned lists, self-added Anki words, do-not-reassign flags) = DATA, verbatim; dated watch-items (false-friend family, gloss slips) = signals policy |
| `week-log.md` | EXEMPT — data table, not signal; lossy compaction destroys it |
| `sessions/` | archive wholesale anything older than the current block; keep files with live undone work in place |
| `00-index.md` | pure map — touch only if the space's structure changed |
| `conventions.md` | operating rules — full strength, untouched |
| `lessons-learned.md` | rules stay full strength with their *why*; incident narratives may archive once their rule + story-kernel are distilled |

## Archive layout

`claude-notes/archive/`, one dated file per source per run:
`archive/YYYY-MM-DD-<source>.md` (e.g. `archive/2026-08-09-learner-model-signals.md`,
`archive/2026-08-09-sessions-2026-07-11-framework-planning.md`). Each run's raw
material stays greppable as a unit. Raw entries are copied **verbatim** — the archive
is the rollback path, not a second summary.

## Verification — no approval gate, invariants + report

The user does not review before the swap (ratified 2026-07-15: archive + git make a
malignant compression recoverable). Instead, self-verify these hard invariants before
finishing — if any fails, fix it before reporting:

1. Every raw dated entry removed from a working file appears **verbatim** in an
   archive file.
2. `learner-model.md` § Baseline diff is **zero**.
3. `week-log.md` is untouched.
4. Vocab registries are intact (compare word lists before/after — no word dropped).
5. Every distilled signal carries its count + last-confirmed-date + exemplar residue.
6. Every open watch-item is marked resolved, live, or **untested-not-resolved** —
   nothing silently dropped.

Then give the user a compact after-action report in chat: what was smoothed, what was
archived, line counts before/after per file. He spot-checks on demand.

---
name: not-working
description: The ejection seat. When a syllabus proves to be a non-fit (too hard, or far too easy) rather than just a bad week, this skill rolls up mid-block progress and triggers a full re-plan via plan-syllabus.
version: 1.0.0
allowed-tools: Read, Write, Edit, Grep, Glob, LS
disable-model-invocation: true
---

This is the ejection seat, and it is distinct from life-happens: life-happens is for *schedule* changes when the plan itself is still right; this skill is for when the plan has proven to be a **non-fit** — usually too hard, less likely far too easy — and continuing to ride these rails is a poor use of study time.

Expect this to be invoked mid-block, typically 1 or 2 weeks into a 4 week syllabus.

## Understand where we went off the rails

Before anything else, ask me questions — one at a time, as more than one question can be overwhelming in the chat — until you fully understand where things went off the rails. For each question, also give me:
- a brief why
- your recommendation

Things worth probing:
- Is the misfit about difficulty (too hard / too easy), pacing, content focus, or format?
- Is it isolated to one thread (readings fine, homework brutal?) or systemic?
- What, if anything, from the current block is worth keeping or finishing?

Consult your ./claude-notes/ space and the lesson-notes.md files from the block so far. The evidence there should inform your questions, and you should reconcile what I tell you with what your **STATE** shows — if I say "too hard" but the homework grades were fine, that mismatch is itself worth a question.

## Roll up progress

Once the diagnosis is clear, roll up the partial block:

- Write clean closing `## Evaluation Notes` into the lesson-notes.md of any lessons we completed.
- Record the ejection in `./syllabus.md` under `## Adjustments`: a dated note that the block was ejected, the diagnosis in a sentence or two, and what was completed vs abandoned. This note is the tombstone; git preserves the full record.
- Delete unstarted lesson folders and readings from the abandoned plan so they do not pollute the clear history — the Adjustments tombstone plus git history covers the record.
- Reconcile vocab: vocab.md is **APPEND ONLY**, so never edit or remove what was appended. Instead, note in your ./claude-notes/ which weeks of vocab were actually studied, and have the re-plan either carry forward the unstudied words or explicitly supersede them in its `## Planning Notes` — never silently duplicate a week.
- Update your ./claude-notes/ **STATE** with the diagnosis: what was misjudged, and what to calibrate differently. This is the single most important input to the re-plan.

## Trigger the re-plan

Then invoke the plan-syllabus skill to generate a fresh 4-week syllabus.
The diagnosis from this skill is a first-class input to that planning session — the new plan should visibly correct for what went off the rails, not simply restart the same gradient.

# Remind Sam

Running list of things we said we'd come back to.

---

## Explore: user-story / iterative-story-completion as the build paradigm for course materials

**Date raised:** 2026-07-14 (Sam), right after the vocab.md grammaticality audit.

**The itch.** Course materials are currently built in big one-shot generations — a whole
syllabus, a whole `vocab.md`, a whole reading — and then audited afterward when something
turns out to be wrong. The *mālō* bug (`Lībertātem servitūtī mālumus`) is the poster child:
one bad sentence, generated in bulk, shipped into Anki, memorized. Post-hoc audits found 25
defects across 292 example sentences. That's a QA process bolted onto a batch process.

**The proposal.** Treat materials-building like a backlog of small, independently
verifiable **stories** instead of a monolithic generation. A story is one unit of work with
a crisp acceptance test:

> "Vocab entry for *mālō*: lemma + principal parts + gloss + ONE example sentence.
> **Done when:** verb governance checked against L&S; macrons verified; headword bolded;
> sentence uses only vocabulary from weeks ≤ N."

Then work the backlog one story at a time, to completion, with the acceptance criteria as
the gate — rather than producing 220 sentences and hoping.

### The "Ralph Wiggum" approach

Sam's shorthand for the loop. The reference is Geoff Huntley's "Ralph Wiggum as a software
engineer": you don't build a clever agent, you build a **deliberately dumb, persistent
one**, and run it in a loop:

```
while true; do  cat PROMPT.md | agent  ; done
```

The character of it:

- **The agent is stupid on purpose.** Each iteration starts with a fresh context and does
  exactly one thing. No long-lived planner trying to hold the whole course in its head.
- **State lives on disk, not in context.** The backlog file *is* the memory. The agent
  reads the plan, picks the next unfinished story, does it, marks it done, exits. Next
  iteration re-reads from scratch. (This is basically what `claude-notes/` and
  `plan-assessment.md` already want to be.)
- **Persistence beats brilliance.** Ralph gets it wrong sometimes; the loop just runs
  again. Errors are self-healing across passes *provided* the acceptance criteria are
  written down and checkable. The loop's stupidity is the feature — it's restartable,
  interruptible, and never gets confused about where it was.
- **Progress is monotonic and visible.** You can walk away and come back to a diff and a
  checklist, not a wall of prose.

### Why this fits *this* project specifically

1. **Bulk generation is where the defects came from.** Every one of the 25 audit findings
   was a sentence written at scale with no per-item gate. A story-shaped workflow forces
   the gate to exist *before* the sentence does.
2. **The acceptance criteria already exist** — we just wrote them, as the defect taxonomy
   in `claude-notes/00-index.md`: (1) check vowel quantities, (2) if it carries a citation,
   pull the source text, (3) check collocation, not just grammar, (4) check verb governance
   against a dictionary. That taxonomy is a **Definition of Done** in disguise.
3. **Sam hand-types vocab into Anki.** The cost of a defect is not "fix it later," it's
   "un-teach it." Per-item verification is worth real tokens here in a way it usually isn't.
4. **A loop can afford to be slow.** Nobody is waiting on it. Overnight, one entry at a
   time, each verified against Perseus/L&S, is entirely affordable — and strictly better
   than one fast pass plus an audit.

### Open questions to work through when we pick this up

- **What's the story granularity?** One vocab entry? One lesson? One reading paragraph?
  (Instinct: one *verifiable artifact* — one vocab entry, one homework question, one
  reading sentence. Small enough that "done" is unambiguous.)
- **Where does the backlog live?** A `stories/` dir? A checklist in `plan-assessment.md`?
  Needs to be greppable and agent-writable, and it needs to survive a fresh context.
- **What's the verification step?** Almost certainly a *separate* agent from the author —
  the audit proved that self-review misses what an adversary catches. But also: the audit
  proved that a **single** reviewer can be confidently wrong (the `tōtō orbe` near-miss,
  where one auditor cited L&S to "fix" a sentence that turned out to be lifted from
  Eutropius). So: author ≠ verifier, and probably verifier ≠ 1.
- **How does a story get marked done, and who's allowed to mark it?** If the author marks
  its own work done, the loop will happily converge on garbage.
- **What's the exit condition?** Ralph runs forever; a syllabus doesn't. Probably: loop
  until the backlog is dry, then a completeness critic asks "what's missing?" and refills it.
- **How does this interact with the existing skills** (`/plan-syllabus`, `/teach-lesson`,
  `/grade-homework`)? Is materials-building a *fourth* mode, or does it replace the
  generation half of `/plan-syllabus`?

### The one-line version

Stop generating course materials in bulk and auditing them after. Generate them one
verifiable story at a time, with the defect taxonomy as the Definition of Done, in a dumb
persistent loop that keeps its state on disk.

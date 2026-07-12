---
name: evaluate-reading
description: This skill is used when I ask you to evaluate the translation I have provided for a piece of daily reading.
version: 1.0.0
allowed-tools: Read, Write, Edit, Grep, Glob, LS
disable-model-invocation: true
---

I will turn in a daily reading file that I have added a translation to, and ask you to evaluate it.
You should only edit the `## Evaluation` part of the file, not my translation directly.
If there is any ambiguity about which file I'm asking you to evaluate, please ask me for clarification rather than making an assumption.

In additon to the evaluation notes you will provide, be sure to use and update your **STATEFUL INFORMATION** in your ./claude-notes/ space.

You may have information in your ./claude-notes/ about why you felt this particular piece or daily reading was useful or why you generated
what you did, so be sure to review your space first before you begin the evaluation.
This way if you gave me a reading because it was a good workout with a specific verb tense, you will have this in your context and
can tailor the evaluation to have a focus on performance related to this.

The evaluation is not a grade or a report card *per se* but should provide a sentence or two about how well the translation aligns to the
latin text in your opinion.
Much of the evaluation will be corrections, alternatives, or even a discussion about mainstream translations that may exist.

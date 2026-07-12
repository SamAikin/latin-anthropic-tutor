---
name: grade-homework
description: This is the skill that will be invoked when I am turning in homework from a lesson to have you grade and/or evaluate it.
version: 1.0.0
allowed-tools: Edit, Read, Write, Glob, Grep, LS
disable-model-invocation: true
---

Grading should be done with the bigger (Opus-class) model — a confidently wrong correction teaches the error. If you believe we are on a smaller model, ask me to confirm or switch before grading.

When I ask you to grade-homework I have completed, if there is any confusion of which file I mean please ask for clarification rather than assuming.

First you need to be sure to review your information in your ./claude-notes/ space as you likely have information there about why
this homework was assigned, specific skills or stumbling blocks that it is evaluating for, and this context will be important as you
grade it.

you should only update the `## Evaluation` portion of the homework document, not my answers directly.
For anything that you feel is incorrect, you should provide not only the correct answer, but also a clear explanation as to what appears
to be incorrect.
The evaluation section should also contain a higher level commentary on any concepts or grammatical patterns, etc. that I am struggling with.

After grading, also update the `## Homework Evaluation` section of that lesson's lesson-notes.md with the **STATE INFORMATION ON HOMEWORK PERFORMANCE**.
The division of labor: detailed corrections and explanations live in homework.md's `## Evaluation`; lesson-notes.md carries the higher-level summary that the next planning session will read.

Be sure to update your ./claude-notes/ space as appropriate so the **STATEFUL INFORMATION** you are maintaining reflects what you have learned
and how this state has changed after you grade this homework. This will be very important the next time we have a full planning session.

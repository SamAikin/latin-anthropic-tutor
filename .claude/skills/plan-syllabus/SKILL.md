---
name: plan-syllabus
description: This is the skill we will use when we need to have a full planning session and to re-generate the `./syllabus.md` file.
version: 1.0.0
allowed-tools: Read, Write, Edit, Grep, Glob, LS, WebSearch, WebFetch
disable-model-invocation: true
---

This is a big effort, and if you believe we are using the wrong model to do it, you should ask me questions and confirm that I'm good with the model invoked.

You should use the files in the `./templates/` directory as needed to ensure the files you are creating and editting are following our agreed upon structure.

In general, this planning will use the following workflow:
- First, compress your notes: read `.claude/skills/compress-notes/SKILL.md` and follow
  that procedure to distill your ./claude-notes/ space before consuming it. The freshly
  distilled space is your planning brief. (Skip only if a compress run already happened
  this session.)
- Read and consider your ./claude-notes/ space
- Read and consider the current `./syllabus.md` file
- Read and consider the lesson-w<nn>-<m> lesson-notes.md files in the time span of the current `./syllabus.md` file.
- Consider any other information you believe is needed after reading and considering the above.
- Ask me questions, one at a time as asking more than one question can be overwhelming in the chat, for anything that is ambiguous to you.
- "re-generate" or replace the `./syllabus.md` file with your new plan, and ask me to review it.
- update as needed based on my feedback until I confirm we have agreed on a syllabus for the next 4 weeks
- generate the daily-readings and lesson-w<nn>-<m> folders and files the 4 week plan will require
- for any daily reading presented as historical text (including reworked historical text), verify the attribution and wording via WebSearch during planning rather than trusting memory — the Provenance section of a reading must be trustworthy, and a subtly wrong attribution poisons it
- update the vocab.md file with the vocab you have choosen, and use `./templates/vocab.template` file as an example of how to append to the vocab.md file.
- ask me to give the updated content a final review
- ensure you update your ./claude-notes/ space as needed so  your **STATEFUL INFORMATION** captures what we decided and did

## First-Run Bootstrap (no history yet)

If `./syllabus.md` is empty and there are no lesson folders yet, this is the first planning session and there is no state to read.
Instead of the history review above:
- Read the learner baseline in ./claude-notes/ (learner-model.md).
- Run a short placement diagnostic in-chat rather than relying on self-report alone: a handful of graded sentences to translate or parse, ramping in difficulty, to find where the rust ends.
- Calibrate the first 4-week block from the diagnostic results, and record them in ./claude-notes/ as the learner model's first real signals.
- For the FIRST block specifically: err on the side of treating me like a beginner, and let me speed run the first 4 weeks. A fast climb up an easy hill beats stalling in front of a wall — the first syllabus is expected to be the poorest fit, and under-shooting difficulty at a brisk pace is the cheaper miss. If it proves far too easy, the not-working skill is the ejection seat.

## Check our Bearings

You likely will want to ask a few questions to ensure the `## North Star` part of our plan is still a good directional bearing.
Be sure to ask questions one at a time, and let me know if you have a recommendation or concern with the North Star.
Remember, the North Star is not what we will accomplish in the next 4 weeks, but is the longer term directional steering: we should be in line with it, not near approaching it.

## Readability

The `./syllabus.md` file is shared contract between us and should very much be a human readable file.
Information that's only for you can go in your ./claude-notes/ space that you are free to utilize how you deem appropriate.
Use the `./templates/syllabus.template` file as an example for you on how to layout out the syllabus file you generate.

## The forever North Star

The goal is language acquisition and study of late republic rome **through the language**.
Tangental aims or goals to this should be questioned.

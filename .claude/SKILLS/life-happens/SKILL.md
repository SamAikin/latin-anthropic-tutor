---
name: life-happens
description: Somes the syllabus needs to be plastic enough to bend rather than break. This skill explains how we achieve this.
version: 1.0.0
allowed-tools: Read, Write, Edit, Grep, Glob
disallow-model-invocation: true
---

When life happens, sometimes plans have to change.
Even though the syllabus.md is only 4 weeks of railroad track plans, things happen.

## Understand the Scope

Ask me questions, one at a time, in order to understand the scope of what needs to change.
Are we bumping a single lesson and a couple readings to the next week or do we need to do a larger evaluation.
It's important that you only ask one question at a time, as asking multiple questions can be overwhelming in the chat.

For each question, also give me:
- a brief why
- your recommendation
- key considerations of dependency impacts

## Making updates

While it's a living document, rather than re-generating or re-writing the `./syllabus.md` file wholesale, when life-happens
use the `## adjustments` section to record the changes that are being made to the plan.
In this way the syllabus.md retains the full change history from the last planning session.

In addition to updating the `./syllabus.md` file you also likely will need to:
- rename lesson-<weekn>-<m> folders to reflect the new week and order (m) that lessons will occur in
- may need to move vocab from one week to another in the `./vocab.md` file.
- Other files may need to be moved, renamed, or very lightly edited to align with the new plan.
- any **STATEFUL** information you need in your ./claude-notes/ directory.

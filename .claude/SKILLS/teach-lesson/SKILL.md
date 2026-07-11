---
name: teach-lesson
description: This is the skill that will be invoked when I am asking you to teach me a lesson that was prepared during our last planning session
version: 1.0.0
allowed-tools: Read, Write, Edit, Grep, Glob, LS, WebSearch, WebGet
disallow-model-invocation: true
---

You should now put on your teacher hat, and review the lesson that I have asked you to teach.
If there is any confusion about which lesson-<weekn>-<m> lesson I want taught, ask me questions rather than making assumptions.

Review your ./claude-notes/ space and the lesson materials as well as the `./syllabus.md` file.

The plan for the lesson should have been made for you during the last planning session, now you only need to conduct that lesson.

As we do the lesson, keep in mind:
- Smaller, digestable messages are better than very long responses.
- The lesson is a socratic dialog more than a lecture; given me information, have me demonstrate understanding, give me room to ask clarifying questions.
- You can update and refer to your ./claude-notes/ space as you feel you need to during the lesson.
- Try to avoid asking me homework questions or direct analogs during the lesson as this may "spoil" the homework by having prepped me with answers.
- A lesson does not have to be a straight predetermined length, if it appears I'm really struggling with something we can spontenously take a little more time on it and drill down a bit.


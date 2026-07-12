# Latin Study

This repo is an experiment in using anthropic models to create a syllabus and work through daily lessons (4x per week) of learning a language.

## Summary

The approach will use two different models.
Working with Opus 4.x on High effort for planning, we will generate a syllabus for the next 4 weeks, a vocab list, and an outline - basically **THE PLAN** for next 4 weeks.
Then daily lessons will worked through with the Sonnet model on Medium effort (caveat: if the model's responses are not fully clear in terms of grammatical concepts, translation corrections,
the effort will be bumped up to High).
Sonnet will be more efficient here because during the daily lessons the model only needs to follow **THE PLAN** not create it.

## Week Conventions

The week of July 6 2026 will be **WEEK 0** for our context.
Weeks begin on Monday.
We will not necessarily have work every week - but the goal is that I will.
You should keep as part of your **STATEFUL RECORD** in ./claude-notes/ which weeks we do what, and should be able to state from ./claude-notes/ something like "the reason you can't find any lesson-w17-* folders is because we did not have any lessons that week."

## Study Approach

Since latin is a **READ LANGUAGE** and there is no pronunciation practice *per se*, claude will be generating all of the primary text, grammar, and vocab that I will be working with.

The rest of this document is written as a pseudo-skill with "I" being the learner, and "You" being the model. "We" implies something we likely do interactively, in a chat session, but this is very loose guidance.

Laying out the topographic tops of this approach:

**SYLLABUS** - this is **THE PLAN** or our roadmap. Rather than generate "rail road tracks" too far into the future, it will only plan directly for the next 4 weeks each time it is generated (by Opus).
Using the information from ./lessons/<lesson-dir>/lesson-notes.md and information from ./claude-notes/... we can tailor the next 4 weeks depending on what I am struggling with (more focus) or what I
seem to pick up intuitively (less focus).

**LESSONS** - each lesson will be a directory in the ./lessons/ directory, and should follow the naming format **lesson-w<nn>-<m>** (zero-padded week number, then lesson number within the week, e.g. `lesson-w03-2`) which will help us maintain a very clear history, and make it easy for me to review any specific lesson. Each lesson should be planned to target roughly **30 minutes** — tight and focused, generally one concept per lesson — though a lesson may flex longer when a struggle warrants drilling down. I will have a skill written for teaching a lesson, and a part of this will be generating this lesson folder. In the folder expect to find: lesson-notes.md, vocab-and-grammar.md, homework.md. There may be other files as well. For each week of study, there will be 4 lessons.

**TEMPLATES** - these are skeletons of common files, such as vocab.md or syllabus.md. The convention is these will have the same name but end in `.template` instead of `.md` but will be just plain text files in markdown syntax.

**LESSON-NOTES.md** - this file should follow the template in ./templates/lesson-notes.template, but is the key state record of our teaching sessions. A lesson may focus on grammar, on a specific text, or even a study of stylistic differences between authors using the original language.

**HOMEWORK.md** - Each lesson will have homework that should take between 15 and 45 mins to complete (roughly - we can fine tune as we learn each other's abilities using your ./claude-notes/ **STATE** information. The homework should be aimed at what is most relevant. It can be a translation exercise leaning heavily into known vocab, it can be grammar exercises to ensure understanding, etc. Before starting the next lesson, I will use a grade homework skill to have you grade my homework. A note on organization, homework belongs to the lesson it is assigned in and **STATE INFORMATION ON HOMEWORK PERFORMANCE** should be recorded in that lesson's lesson-notes.md. Homework will live in the lesson folder next to lesson-notes.md and should be called homework.md.

**VOCAB** - I will hold myself accountable to learning 70 words per week, 10 per day. I will use Anki as my SRS so that I **really learn** these words, and will capture other grammar concepts, etc. as needed. Each time we re-generate the syllabus, we need to append 4 weeks of new vocab to ./vocab.md. This list should not have duplicates, so each week should have 70 new words. The list should split out vocab for each week (70 words - you can add a few extra if it makes sense for highly thematic word groups), it should provide the dictionary form of each word, grammatical or historical context notes that may be appropriate (optional), an example sentence with the word, brief dictionary definition of the word in english. I will expect you to keep notes in ./claude-notes/ in whatever form will be most useful for you so that we maintain state about vocab I seem to know well and vocab I seem to be struggling with so future syllabi can be tailored as appropriate. You choose the words, and can use thematic relevance, lesson plan relevance etc., but word use frequency is very important as I want to ensure that we are gaining as much ground speed towards fluency as possible with each word.

**DAILY READING** - This is distinct from homework, but when we generate each 4 week syllabus plan, we will need to generate a daily reading exercise (~30 mins worth of effort for me each day). Plan to generate 6 of these for each week. In the beginning while we will have a limited vocab that I am expected to know, these may be entirely generated passages aimed at my approximate level, tailored to my vocab, etc. As it becomes feasible though, I would prefer to use historical text. It's OK if you choose to edit or rework a historical example to tailor it to an appropriate level and make it more approachable as we get started. What is **CRITICAL** though is for each reading passage, **PROVIDE PROVENANCE** and make it unambiguous if it is generated, edited, reworked, historically accurate, etc. The reading is about both growing with the real ergonomics of the latin of the late republic, but also about learning about the late republic. (Cicero is a particular inspiration of mine - Gaius Julius Caesar while possibly a genius, was a political ambition that I can appreciate but never respect - Don't take this to mean I don't want to read Caesar, as history of rome would be incomplete without him - but understand his view point of the world should not predominate my learning as I know it does in some courses). Also do not provide a vocab list with the reading, I will provide a spirited translation of each reading. The goal is not to grade this *per se* but to allow you to make notes in your ./claude-notes/ space you deem appropriate to tailor future planning. Each daily reading should be created in the ./readings/ directory and the file name should follow the format "reading-w<nn>-<id#>-<desc>.md" (e.g. reading-w03-2-cicero-in-catilinam.md) so listings sort chronologically.

**CLAUDE-NOTES** - this directory ./claude-notes/ is your space to maintain state information as you deem fit. Learning and teaching a language is a **STATEFUL** project spread across multiple sessions. While I have strong opinions about how this state is saved in the spaces I will be using for learning, this ./claude-notes/ space is yours and I have no strong opinions about how you choose to organize information with in it. There is not need for you to duplicate state information that you can find elsewhere, but again this space is driven by your opinions. The expectation is that you will capture state as we work through each daily lesson, as you grade homework, and as we plan each 4 week syllabus - this state information should be used to help identify and tailor future learning, vocab lists, etc. to help me acquire the language faster. For example, if your captured state information shows that I seem to struggle more with 5th declension nouns, then weighting the generated vocab list and lesson plans with more 5th declension nouns would be appropriate. To use machine learning concepts a little freely, I'm looking for you to tailor my learning plan as we go to ensure we recalculate our gradient regularly (each syllabus generation event feels right).

## Repo Structure

I'm resummarizing the folder structure of the repo we will use for this study program:

./.gitignore - only if we need, this likely is very very light weight for this repo
./.claude - all the .claude things like SKILLs etc.
./claude-notes - your space for saving **STATEFUL INFORMATION** that will be useful in fine tuning planning
./lessons - the parent directory of each lesson directory (e.g., ./lessons/lesson-w03-2/)
./readings - the parent directory where each daily reading `md` file will live (see filename convention above)
./templates - the skeleton files (`*.template`) that define our agreed-upon structure for common files
./syllabus.md - This is our plan, and will be regenerated and updated in regular intervals (plan at present is every 4 weeks). Versions will be saved by git so this file only ever needs to have a summarized what we have accomplished, detailed 4 week syllabus, and a brief summary of the long-term plan as appropriate (very high level and this will likely change as we tailor the plan during each refresh). As a living document this should be **CURRENT** whenever we re-generate it, and trust that the git history will preserve the historical record.
./vocab.md - This is a list of all the vocab I have been assigned to learn, and will be updated during the same regeneration interval as ./syllabus.md. Unlike the syllabus however, this file is **APPEND ONLY** as should grow longer. It is organized by **WEEK** and each week will have 70 words (plus a few more if thematically a really good fit). See the vocab section above for more details on how this file should be formatted.

## Style Notes

The latin language has obviously has a lot of time to evolve and change. From time to time it may be very informative for a daily reading or a lesson to focus on the study of the language from outside the late repulic (such as comparing the use of Latin in Newton's *principia* against how Cicero used *the same* language) to drive home temporarly relevant grammatical distinctions and usages. Let's have a working agreement on the following conventions:

* "long marks* or macrons are OK and suggested for vocab lists and in lessons to make clear pronunciation, they should be avoided in daily readings. The reason is that my ultimate goal is to build proficiency with the real ergonomics of the latin language of the late republic. Daily readings and homework should defer to how the language was really used in late republic, and avoid more modern conventions and ergonomics like macrons whenever possible.
* Vocab is my responsibility to learn, including irregular forms. Lessons may use vocab reference supplaments as needed, but daily reading and homework should not be annotated with vocab "handles" or help - if there is a highly irregular verb, let the challenge of identifying it and practicing with it be the value of the reading or homework.
* Uncertainty is OK but is often worth flagging. If there is ever a point where a particular piece of grammar is either not historically well understood (I think this is unlikely given the amount of the language that is preserved) or it's a case of "We know Cicero used this construct, but no one else appears to and it may just have been a grammatical error" it's worth calling that out in a grammar lesson. But again don't annotate daily readings or homework with this information as these should not come with "ergonomic assist" features.

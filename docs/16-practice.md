# 16. Practice: fourteen hands-on exercises

[Home](../README.md) | Previous: [Harness engineering](15-harness-engineering.md) | Next: [Quick reference](17-quick-reference.md)

![Person working at a desk with a laptop](https://images.unsplash.com/photo-1515879218367-8466d910aaa4?w=1200&q=80&auto=format&fit=crop)
<sub>Photo: Chris Ried on Unsplash</sub>

Each exercise lists the surface, a suggested model, the time it takes,
what it teaches, the exact steps, and how to tell you succeeded. All data
is invented. Do them in order, or jump to the level you need.

| # | Exercise | Surface | Level |
|---|---|---|---|
| 1 | Brief vs vague | Chat | Beginner |
| 2 | Messy list to clean spreadsheet | Chat | Beginner |
| 3 | Build and share an artifact | Chat | Beginner |
| 4 | Catch a hallucination | Chat | Beginner |
| 5 | Set up a project | Chat | Intermediate |
| 6 | Connect a calendar | Chat + connector | Intermediate |
| 7 | Create and test a skill | Chat | Intermediate |
| 8 | Hand off a folder task | Cowork | Intermediate |
| 9 | First Claude Code session | Claude Code | Advanced |
| 10 | Plan mode on a real change | Claude Code | Advanced |
| 11 | Write your CLAUDE.md layers | Claude Code | Advanced |
| 12 | Schedule a routine | Claude Code (cloud) | Advanced |
| 13 | Interview me into a spec | Chat or Claude Code | Intermediate |
| 14 | Writer and reviewer | Claude Code | Advanced |

---

## Exercise 1 - Brief vs vague

**Surface:** Chat | **Model:** Sonnet | **Time:** 5 min
**Teaches:** how much context changes the result.

1. New chat. Send: `Plan a dinner party.`
2. New chat. Send:

   ```text
   Plan a dinner party for 6 adults this Saturday. One guest is vegan and
   one can't eat nuts. My budget is 60 in total, I have one oven and four
   hobs, and I want to spend no more than 90 minutes cooking on the day.
   Give me a menu, a shopping list grouped by shop section, and a timeline
   starting from 4pm.
   ```

3. Correct it once: `Swap the dessert for something I can make on Friday.`

**Done when:** the second plan respects every constraint (vegan option,
no nuts, budget, oven limit), and the correction changes only the dessert
and its timeline entries.

---

## Exercise 2 - Messy list to clean spreadsheet

**Surface:** Chat | **Model:** Sonnet | **Time:** 6 min
**Teaches:** describing the problem and the output format together, and
asking for gaps to be flagged.

1. Paste this:

   ```text
   book club members (export)
   name;joined;fav genre;email ok?
   Rowan P.;2024-03-01;sci-fi;yes
   Mika T.;01/05/2024;Mystery;Y
   ;;;
   Jo Alvarez;May 2024;;no
   Priya N.;2024/06/15;fantasy;yes
   Sam K.;;history;y
   ```

2. Ask:

   ```text
   Turn this into a clean Excel file: headers on row 1, remove empty rows,
   dates as YYYY-MM-DD, genre in Title Case, and "email ok?" as TRUE/FALSE.
   Where a value is missing or ambiguous, leave it blank and list it on a
   second sheet called "Check" with the reason. Don't guess missing values.
   ```

**Done when:** you get an `.xlsx`; Sam's missing date and Jo's missing
genre (and the vague "May 2024") appear on the Check sheet instead of being
invented.

---

## Exercise 3 - Build and share an artifact

**Surface:** Chat | **Model:** Sonnet | **Time:** 10 min
**Teaches:** artifacts, iteration and sharing.

1. Ask:

   ```text
   Create an interactive artifact: a 25-minute focus timer (Pomodoro) with
   start, pause and reset, a 5-minute break mode, a count of completed
   sessions, and a gentle sound at the end. Accessible colours and large
   buttons.
   ```

2. Test it in the panel. Then iterate: `Add a task name field, and keep a
   list of the tasks finished today.`
3. Find it under **Artifacts** in the sidebar, and use the share controls to
   create a link. Open the link in a private browser window.

**Done when:** the timer works, the link opens for someone else, and you
know how to turn sharing off again.

---

## Exercise 4 - Catch a hallucination

**Surface:** Chat | **Model:** Opus | **Time:** 8 min
**Teaches:** grounding and "not stated" answers.

1. Paste this fictional product sheet:

   ```text
   TRAILMATE 2 WATER BOTTLE - PRODUCT SHEET (fictional)
   Capacity: 750 ml. Material: stainless steel, double-walled.
   Keeps drinks cold for up to 24 hours. Dishwasher safe (lid hand-wash only).
   Warranty: 2 years against manufacturing defects.
   ```

2. Ask: `Is the Trailmate 2 safe for hot drinks, how heavy is it, and does
   the warranty cover dents? Answer only from the sheet, quote the line you
   used, and say NOT STATED where the sheet doesn't say.`

**Done when:** it says NOT STATED for hot drinks and weight, and explains
that the warranty covers *manufacturing defects* (so dents are probably not
covered, and it should say that is an inference, not a quote).

---

## Exercise 5 - Set up a project

**Surface:** Chat | **Model:** Sonnet | **Time:** 10 min
**Teaches:** project instructions and knowledge.

1. **Projects > + New project**, name `Learn Spanish`.
2. Instructions:

   ```text
   I'm an A2-level Spanish learner. Reply in simple Spanish first, then an
   English translation in italics. Correct my mistakes gently at the end of
   each reply in a short "Correcciones" list. Focus on travel and food
   vocabulary.
   ```

3. Add knowledge: paste a list of 20 words you are learning.
4. New chat in the project: `Hola, quiero pedir comida en un restaurante.`

**Done when:** replies follow the format automatically and use your word
list, without you repeating the instructions.

---

## Exercise 6 - Connect a calendar

**Surface:** Chat + connector | **Model:** Sonnet | **Time:** 10 min
**Teaches:** connectors, per-chat toggles, read vs write.

1. **Customize > Connectors > +**, connect your calendar and sign in.
2. New chat, **+ > Connectors**, enable only the calendar.
3. Ask: `What does my next week look like? Find two 1-hour gaps for exercise.`
4. Ask: `Add the first gap as a private event called "Run".`
5. Watch for the confirmation step before it writes.

**Done when:** the answer matches your calendar, and the event is created
only after you approve. Delete the test event yourself afterwards if you
like.

---

## Exercise 7 - Create and test a skill

**Surface:** Chat | **Model:** Opus to build, Sonnet to use | **Time:** 15 min
**Teaches:** skill descriptions and trigger testing.

1. **Customize > Skills > + > Create skill > Create with Claude.**
2. Ask for:

   ```text
   A skill that turns any set of study notes into 10 flashcards: question,
   answer, and a difficulty tag (easy/medium/hard), output as a CSV table I
   can import into a flashcard app. It should not be used for general
   summaries or essays.
   ```

3. Answer its questions, then save the skill.
4. Test these in fresh chats (paste a paragraph of notes with each):
   - Should use it: `make flashcards from this`, `quiz me on these notes`,
     `turn this into revision cards`.
   - Should not: `summarise these notes`, `write an essay from this`,
     `fix the grammar in this paragraph`.

**Done when:** it loads for the first three and not the last three. If not,
edit the description and repeat.

---

## Exercise 8 - Hand off a folder task

**Surface:** Cowork | **Model:** Sonnet | **Time:** 15 min
**Teaches:** folder scoping, approval modes, reviewing a plan.

1. Create a folder `recipes-practice` with 5 text files, each containing a
   recipe (ask Claude in a normal chat to generate five short fictional
   recipes if you don't have any).
2. Start a Cowork task on that folder, mode **Ask before acting**:

   ```text
   Read every recipe. Create cookbook.docx with a contents page, one recipe
   per page with a consistent layout, and a combined shopping list at the
   end grouped by aisle. Keep the original files unchanged.
   ```

3. Read the plan before approving. Approve each step.

**Done when:** `cookbook.docx` exists with all five recipes and a shopping
list, and the original files are untouched.

---

## Exercise 9 - First Claude Code session

**Surface:** Claude Code (terminal or IDE) | **Model:** Sonnet | **Time:** 15 min
**Teaches:** orientation, running tests, reviewing diffs.

1. Create a sample project:

   ```bash
   mkdir todo-cli && cd todo-cli && git init
   claude
   ```

2. Ask:

   ```text
   Create a small Python command-line to-do app: add, list, done and remove
   commands, storing tasks in a JSON file. Include pytest tests and a
   README. Keep it under 150 lines of app code.
   ```

3. Approve the steps (Manual mode) and watch what it runs.
4. Ask: `Run the tests and show me the results.`
5. Ask: `Commit this on a new branch called feature/initial-app.`

**Done when:** tests pass, you have read the diff, and the commit is on a
branch rather than `main`.

---

## Exercise 10 - Plan mode on a real change

**Surface:** Claude Code | **Model:** Opus for planning | **Time:** 15 min
**Teaches:** planning, reviewing and amending before code changes.

1. In the `todo-cli` project, press `Shift+Tab` until you see
   `plan mode on`.
2. Ask:

   ```text
   Add due dates to tasks (optional, YYYY-MM-DD), a "list --overdue"
   option, and tests. Show me the files you'll change, the approach and the
   risks before writing anything.
   ```

3. Review the plan with the questions from [chapter 12](12-plan-mode.md).
   Choose **No, keep planning** and give one correction (for example
   `Store dates as ISO strings and reject invalid dates with a clear error`).
4. Approve with **Yes, manually approve edits** and review each edit.
5. Run the tests.

**Done when:** the final change matches the amended plan and all tests pass.

---

## Exercise 11 - Write your CLAUDE.md layers

**Surface:** Claude Code | **Model:** Sonnet | **Time:** 10 min
**Teaches:** project, local and user memory files.

1. In `todo-cli`, run `/init` and review the generated `CLAUDE.md`. Trim it
   to the essentials: how to run, how to test, conventions.
2. Add a rule: `Every new command must have a test and a README entry.`
3. Create `CLAUDE.local.md` with a personal note, and add it to
   `.gitignore`.
4. Add one line to `~/.claude/CLAUDE.md`, such as
   `Always explain the plan in 3 bullet points before large changes.`
5. Run `/memory` to see all loaded files. Start a new session (or `/clear`)
   and ask for a new `search` command.

**Done when:** Claude adds a test and README entry without being asked,
and follows your user-level preference.

---

## Exercise 12 - Schedule a routine

**Surface:** Claude Code routines (cloud) | **Model:** Sonnet | **Time:** 15 min
**Teaches:** unattended runs, triggers, least-privilege connectors.

1. Push `todo-cli` to a **personal** GitHub repository.
2. Go to [claude.ai/code/routines](https://claude.ai/code/routines) >
   **New routine**.
3. Prompt:

   ```text
   Check the repository for TODO comments and failing tests. Open a single
   GitHub issue titled "Weekly health check" listing what you found. If
   nothing is found, do nothing. Never push to main or merge anything.
   ```

4. Select the repository, the Default environment, a **weekly** schedule,
   and **remove all connectors** that are not needed.
5. **Create**, then **Run now**.
6. Open the run and read the transcript.

**Done when:** the run completes, you understand exactly what it did, and
no code was pushed to `main`. Pause or delete the routine afterwards if you
do not want it running weekly.

---

## Exercise 13 - Interview me into a spec

**Surface:** Chat, or Claude Code | **Model:** Opus | **Time:** 15 min
**Teaches:** question-first prompting and writing a reusable spec.

1. Pick something you want built or planned (an app feature, a garden
   redesign, a birthday party, a study plan).
2. Send only a one-line description plus:

   ```text
   Interview me before doing anything. Ask one short batch of questions at
   a time, most important first, and dig into the hard parts I might not
   have thought about (edge cases, constraints, trade-offs). When you have
   enough, write a one-page spec: goal, requirements, out of scope, open
   questions, and how we'll know it's done.
   ```

   In Claude Code, add `using the AskUserQuestion tool` and `write it to
   SPEC.md`.
3. Answer its questions honestly, including "I don't know".
4. In a **fresh** chat (or after `/clear`), paste the spec and ask for the
   plan or implementation.

**Done when:** the spec contains at least one requirement or risk you had
not thought of before the interview, and the fresh session can act on it
without asking you to re-explain.

---

## Exercise 14 - Writer and reviewer

**Surface:** Claude Code | **Model:** Sonnet to write, Opus to review | **Time:** 15 min
**Teaches:** independent verification with a fresh context.

1. In the `todo-cli` project from exercise 9, ask:
   `Add a "search" command that finds tasks containing a word, case-insensitive, with tests.`
2. When it is done, **do not** ask the same session if it is correct.
   Instead:

   ```text
   Use a subagent to review the diff for the search command. Check edge
   cases (empty query, special characters, no matches, unicode), test
   coverage, and consistency with the other commands. Report only issues
   that affect correctness, with file and line.
   ```

3. Paste the findings back: `Here is the review. Fix the real issues and
   rerun the tests.`
4. Optional: run `/code-review` and compare what it finds.

**Done when:** the reviewer found at least one real gap (or clearly
explained why there were none), fixes are made, and tests pass.

---
[Home](../README.md) | Previous: [Harness engineering](15-harness-engineering.md) | Next: [Quick reference](17-quick-reference.md)

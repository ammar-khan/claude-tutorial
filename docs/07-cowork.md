# 7. Cowork: hand over the whole task

[Home](../README.md) | Previous: [Hallucinations](06-hallucination.md) | Next: [Skills](08-skills.md)

![Person writing a list in a notebook](https://images.unsplash.com/photo-1484480974693-6ca0a78fb36b?w=1200&q=80&auto=format&fit=crop)
<sub>Photo: Glenn Carstens-Peters on Unsplash</sub>

Chat is one question, one answer. **Cowork** is for outcomes: you describe
what you want, Claude makes a plan, works through it step by step (reading
files, using connectors, browsing, building documents) and comes back with
finished work. It is available on paid plans, on desktop, web and mobile.

## Chat vs Cowork

| | Chat | Cowork |
|---|---|---|
| Shape | Question and answer | Multi-step task with a plan |
| Reaches | What you paste or attach | A folder you choose, connectors, the browser |
| You | Stay and iterate | Can step away and come back |
| Example | "Rewrite this paragraph." | "Read the 30 survey responses in this folder, group the feedback into themes, and build a slide deck with the top five." |

## Starting a task

- **Latest UI:** there is no separate mode to pick. Just describe the
  task in a normal conversation. Claude switches into working through
  steps when the job calls for it.
- **Earlier layout:** choose **Cowork** in the message box, or the Cowork
  tab of the desktop app.

### Step by step

1. Click **Work in a project or folder** in the prompt bar and pick a
   folder. Claude can read and write **only** inside it. Use a dedicated
   working folder, not your whole Documents.
2. Pick the approval mode:
   - **Ask before acting** (manual, the default) - safest; use it for
     anything important or irreversible.
   - **Auto** - Claude proceeds and a safety check blocks risky actions.
   - **Skip** (no prompts) - only for low-risk, well-understood jobs.
   Whatever the mode, Claude asks before **permanently deleting** a file.
3. Describe the outcome clearly:

   ```text
   The "survey" sub-folder has one text file per customer response.
   Group the feedback into themes and count how many responses mention
   each. Create themes.xlsx (theme, count, two example quotes) and a
   five-slide deck, top-themes.pptx, one slide per top theme.
   Quote customers exactly; don't paraphrase inside quotation marks.
   Don't change or delete anything in "survey".
   ```

4. Watch the plan and progress panel. Step in if it drifts.
5. Review the result before you use it.

## Scheduled tasks

Anything you do regularly can run on a schedule:

1. Click **Scheduled** in the sidebar > **New task** (or type `/schedule`).
2. Choose **Create with Claude** (describe it) or **Set up manually**: name,
   prompt, approval mode, frequency (hourly, daily, weekdays, weekly or
   manual), model and folder.
3. **Save.** Past runs are listed so you can review what happened.

Tasks that need local files run only when your computer is on and the app
is available. For work on code repositories that should run in the cloud,
see [Routines](14-routines.md).

## Using Cowork safely

Based on Anthropic's
[Cowork safety guidance](https://support.claude.com/en/articles/13364135-use-claude-cowork-safely):

- Give it **the smallest folder** that does the job; keep sensitive files
  out.
- Use **manual approval** for high-stakes or irreversible work.
- **Only allow websites you trust.** Web pages and documents can contain
  hidden instructions ("prompt injection"). Claude is trained to ignore
  them, but limiting what it reads is the best defence.
- **Vet plugins and connectors** before installing.
- Start scheduled tasks on **low-risk** jobs and review their first runs.
- **Stop** a task that behaves unexpectedly. You remain responsible for
  what Claude does on your behalf.

## Claude in Chrome

The **Claude in Chrome** extension (paid plans) lets Claude read the page
you are on, click, navigate and fill forms, from a side panel. Great for
"collect the prices from these five tabs into a table". The same safety
rules apply: allow it only on sites you trust, and review before it submits
anything.

## Try it now (15 minutes)

1. Make a folder called `cowork-practice` and copy in 10 to 20 files of
   mixed types you don't mind Claude seeing (photos, PDFs, text files).
2. Start a task with that folder:
   `Organise this folder: create sub-folders by file type, move each file
   into the right one, and write index.md listing every file with its new
   location and a one-line description. Show me the plan before moving
   anything. Don't delete or rename any file.`
3. Keep approval on **Ask before acting**, read the plan, then approve.
4. **Done when:** every file is in a sub-folder, nothing was deleted or
   renamed, and `index.md` lists them all. Compare the count with what you
   started with.

---
[Home](../README.md) | Previous: [Hallucinations](06-hallucination.md) | Next: [Skills](08-skills.md)

# 3. Artifacts and real files

[Home](../README.md) | Previous: [Chat and prompting](02-chat.md) | Next: [Projects and memory](04-projects.md)

![Code editor on a screen](https://images.unsplash.com/photo-1619410283995-43d9134e7656?w=1200&q=80&auto=format&fit=crop)
<sub>Photo: Juanjo Jaramillo on Unsplash</sub>

Besides replying in the chat, Claude can produce standalone results. There
are two kinds:

| | Artifact | Real file |
|---|---|---|
| What | A page that opens in a panel next to the chat: a document, chart, dashboard, checklist, calculator, small web app, diagram. | An actual `.docx`, `.xlsx`, `.pptx`, `.pdf`, `.csv` or image you download. |
| Share by | A link (you control who can see it). | Sending the file. |
| Best for | Interactive or visual things; something to show people. | Anything that must live in Office, be printed or attached to an email. |

## Switch it on (usually already on)

Both need **Settings > Capabilities > Code execution and file creation**
turned on. On Team/Enterprise plans an admin may control this.

## Getting a real file

Name the file type you want and describe its structure:

```text
Create an Excel workbook that tracks my monthly household budget:
one sheet per month, categories down the side, a totals row with
working formulas, and a summary sheet with a chart.
```

Claude writes and runs code behind the scenes to build the file, then
gives you a download card. Things it can make: Word (real headings and
tables), Excel (working formulas), PowerPoint (layouts and speaker notes),
PDF (new, or filling in an existing form), CSV and PNG charts.

**Tips**

- Upload a file and ask for an edited copy: `Keep the original; save the
  cleaned version as a new file.`
- Ask for formulas, not typed-in numbers, so the sheet keeps working.
- Files up to roughly 30 MB each can be uploaded.

## Getting an artifact

Ask for something visual or interactive:

```text
Make an interactive artifact: a tip calculator where I enter the bill,
pick a tip percentage with a slider, and split it between N people.
Clean, mobile-friendly design.
```

The artifact opens beside the chat. You can:

- **Iterate** - `Make the buttons bigger and add a dark mode.`
- **See the code** - switch between preview and code.
- **Find it later** - every artifact is listed under **Artifacts** in the
  left sidebar, which also offers starter templates (for example slides,
  documents and designs).
- **Share it** - artifacts start **private**. Use the share controls to
  publish a link. On personal plans a published artifact can be viewed by
  anyone with the link; on business plans sharing is limited to your
  organisation. You can also get an embed code.

### AI-powered artifacts

An artifact can call Claude itself, for example a flashcard app that
generates new questions, or a writing coach. When someone else uses a
shared AI-powered artifact, the usage counts against **their** account, not
yours. New artifacts ask before calling Claude's API.

### Live artifacts with connectors

On supported plans, an artifact can pull live data from your connectors
(for example "a dashboard of my open tasks"), so it refreshes when you
open it rather than showing a frozen snapshot.

## Try it now (7 minutes)

1. In a new chat, ask for an interactive tool:
   `Build an artifact: a reading tracker where I can add a book (title,
   author, pages, date finished), see a running total of pages, and a bar
   chart of books finished per month. Keep the data in the page while I
   use it.`
2. Add a few made-up books and check the total and chart update.
3. Iterate: `Add a filter by author and a "clear all" button that asks
   for confirmation.`
4. Now ask for a file instead: `Give me an .xlsx template with the same
   columns, a pages total formula, and a second sheet that counts books
   per month with COUNTIFS.`

**Done when:** you have a working artifact you could share by link, and an
Excel file whose totals change when you type in new rows.

---
[Home](../README.md) | Previous: [Chat and prompting](02-chat.md) | Next: [Projects and memory](04-projects.md)

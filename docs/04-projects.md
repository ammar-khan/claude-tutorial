# 4. Projects, instructions and memory

[Home](../README.md) | Previous: [Artifacts and files](03-artifacts.md) | Next: [Connectors](05-connectors.md)

![Books on a wooden shelf](https://images.unsplash.com/photo-1524995997946-a1c2e315a42f?w=1200&q=80&auto=format&fit=crop)
<sub>Photo: Susan Q Yin on Unsplash</sub>

A new chat starts with no knowledge of your earlier ones. Claude has three
features for carrying context forward, from broadest to narrowest:

| Feature | Scope | Use it for |
|---|---|---|
| **Instructions for Claude** | Every chat you have | How you like to be written to: language, tone, length. |
| **Memory** | Across chats (and per project) | Facts Claude picks up about you and your work over time. |
| **Projects** | One stream of work | Files, instructions and chats for a specific job, client, course or hobby. |

## Instructions for Claude (personal preferences)

Where: **Settings > General** in the latest UI (older layouts: your
profile, or Customize).

Example:

```text
I'm a secondary school science teacher. Use British English.
Keep answers short unless I ask for detail. Prefer prose to bullet lists.
Tell me when you're unsure instead of guessing.
```

You write these once, and every new chat uses them.

## Memory

- **Settings > Memory** shows what Claude remembers, grouped by topic. You
  can edit or delete any of it.
- **Settings > Capabilities** has the switches to generate memory from
  chat history and to let Claude search and reference past chats.
- Each **project has its own memory**, so what you discuss in a work
  project does not leak into a personal one.
- Use an **incognito chat** when you do not want something remembered.

## Projects

A project is a folder-like workspace. Everything inside it starts already
knowing your context.

### Create one, step by step

1. In the left sidebar click **Projects**, then **+ New project**.
2. Give it a name and a one-line description, for example
   `Allotment planner - planting schedules and budget`.
3. Click **Set project instructions** and paste standing instructions:

   ```text
   You're helping me plan a small vegetable allotment in a temperate
   climate. Always give quantities in metric. Assume I'm a beginner.
   When you suggest plants, include sowing month and spacing.
   Flag anything that needs a greenhouse.
   ```

4. Add **project knowledge**: click **+** in the knowledge area and upload
   files (a plot plan, seed list, last year's notes) or paste text.
5. Start a chat **inside the project**. Ask something small, like
   `What should I sow next month?`. It should already know your setup.

### Good to know

- On paid plans, project knowledge automatically expands beyond the
  normal context size by searching your files (retrieval), so large
  projects still work.
- The Free plan allows a small number of projects; paid plans allow more.
- You can move an existing chat into a project, star projects, and
  archive old ones from the three-dot menu.
- On Team/Enterprise plans you can **Share project** with colleagues
  (**Can view** or **Can edit**). Give edit access only to people who need
  it.

## Which one should I use?

- Something about **you** in general? Put it in **Instructions**.
- Something about **one piece of work**? Put it in a **Project**.
- A **procedure** you repeat ("how I format my weekly report")? That is a
  **Skill** ([chapter 8](08-skills.md)).

## Try it now (8 minutes)

1. Add personal instructions (the teacher example above, edited to be
   about you).
2. Create a project called `Trip planning` with the instruction: `Always
   show costs in my home currency and flag anything that needs booking
   more than a month ahead.`
3. Upload or paste a short list of places you would like to visit.
4. Open a new chat in the project and ask: `Suggest a 3-day plan.`
5. **Done when:** it uses your currency and flags bookings without you
   mentioning either.

---
[Home](../README.md) | Previous: [Artifacts and files](03-artifacts.md) | Next: [Connectors](05-connectors.md)

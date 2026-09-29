# 2. Chat and prompting

[Home](../README.md) | Previous: [Getting started](01-getting-started.md) | Next: [Artifacts and files](03-artifacts.md)

![Yellow sticky notes on a wall](https://images.unsplash.com/photo-1585692614056-d0bbd2d5069b?w=1200&q=80&auto=format&fit=crop)
<sub>Photo: Nathan Dumlao on Unsplash</sub>

Chat is the simplest way to use Claude: type a message, get a reply. Most
weak answers come from missing information, not from a weak model.

## Write a clear brief

![Anatomy of a good prompt](../images/diagrams/prompt-anatomy.svg)

Claude only knows what is in the conversation. Anything in your head
(who the reader is, what happened last week, what you already tried) has to
be written down. A useful checklist:

1. **Task** - what you want made or done.
2. **Context** - the facts they cannot know unless you say them.
3. **Audience and tone** - who reads it, how it should sound.
4. **Format and "done"** - length, structure, file type, what finished looks like.

### Before and after

| Vague | Specific |
|---|---|
| `Give me a workout plan.` | `I'm 45, a beginner, and have 30 minutes on Monday, Wednesday and Friday with only a pair of dumbbells at home. Give me a 4-week plan that builds up gradually, as a table, with one sentence on form for each exercise.` |
| `Explain recursion.` | `Explain recursion to a 14-year-old who knows basic Python loops. Use one everyday analogy, then a 6-line code example, then a common mistake to avoid. Under 250 words.` |
| `Help with my cover letter.` | `Here is a job ad and my CV. Write a cover letter under 300 words that links my two most relevant projects to their top three requirements. Confident, not boastful. Don't invent any experience that isn't in my CV.` |

The longer versions are not "prompt engineering". They simply include
the facts, the reader and the finish line that the short versions left out.

## Iterate on the answer

Treat the first reply as version one and give feedback on it, the way you
would with a human draft:

- `Too long. Three bullets.`
- `The second paragraph is too apologetic - make it confident.`
- `You missed the budget point. Add it before the conclusion.`
- `Good. Now make a version for a non-technical reader.`

Quick, specific feedback is usually faster than trying to write the
perfect prompt up front.

## Tools inside the message box

Click **+** at the bottom left of the message box:

| Option | What it does |
|---|---|
| **Add files or photos** | Attach PDFs, Word/Excel files, images, CSVs. You can also drag and drop. |
| **Connectors** | Toggle which connected apps this chat may use (see [chapter 5](05-connectors.md)). |
| **Research** | A deeper, multi-search investigation that returns a cited report (paid plans; takes a few minutes). You can also type `/deep-research`. |
| **Web search** | Lets Claude look things up. In the latest UI it runs automatically when helpful. |
| **Skills** | Pick a skill to use explicitly (see [chapter 8](08-skills.md)). |

Next to the send button:

- **Model picker** - choose Haiku, Sonnet, Opus or Fable.
- **Effort** - hover over it to set Low to Max, and toggle extended
  **Thinking** on models that allow switching it off.

## Other chat features worth knowing

- **Incognito chat** - click the ghost icon at the top of a new chat. It is
  not saved to your history or memory. Useful for one-off, sensitive
  questions.
- **Memory** - Claude can remember useful things about you across chats.
  Manage it under **Settings > Memory** (see and delete what it remembers)
  and **Settings > Capabilities**.
- **Instructions for Claude** - your standing preferences ("British
  English, be concise, no emojis"). In the latest UI they live in
  **Settings > General**; older layouts have them under your profile.
- **Starring chats** - star a conversation that went well so you can find
  and reuse it.
- **Voice** - on mobile and desktop you can dictate or have a voice
  conversation.

## What goes in, and what should not

A sensible default is to share only what you would be comfortable
putting in any online service:

- Fine: your own drafts, public information, made-up examples.
- Think twice: other people's personal details, anything confidential,
  passwords, bank details, medical records.
- Never paste secrets such as passwords or API keys.

## Try it now (5 minutes)

1. Open a new chat and send the thin prompt: `Write a birthday message.`
2. Now send a proper brief: `Write a birthday message for my neighbour
   Sam, who is turning 70 and loves gardening. Warm, a little funny, two
   sentences, to go in a card.`
3. Correct it: `Less formal, and mention tomatoes.`
4. Compare the three results. That gap is the whole lesson.

---
[Home](../README.md) | Previous: [Getting started](01-getting-started.md) | Next: [Artifacts and files](03-artifacts.md)

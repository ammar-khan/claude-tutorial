# 18. Quick reference

[Home](../README.md) | Previous: [Practice](17-practice.md)

## Which feature do I need?

| I want to... | Use |
|---|---|
| Ask a question or get a draft | Chat |
| Get a Word/Excel/PowerPoint/PDF file | Chat (name the file type) |
| Get something interactive or shareable by link | Artifact |
| Stop re-explaining my preferences | Settings > General (instructions) and Memory |
| Keep files and instructions for one piece of work | Project |
| Let Claude read my mail, calendar, drive, tracker | Connector |
| Teach Claude a repeatable procedure | Skill |
| Install a ready-made bundle of skills and connectors | Plugin |
| Hand off a multi-step task with files | Cowork |
| Automate something in the browser | Claude in Chrome |
| Work on code in a repository | Claude Code |
| Run Claude on a schedule | Scheduled tasks (local) or Routines (cloud) |

## Prompt templates

| Goal | Template |
|---|---|
| Summarise | `Summarise [thing] for [reader] in [length]. Focus on [what matters]. List any deadlines.` |
| Write | `Draft a [type] to [who] about [topic]. Tone: [tone]. Must include [points]. Under [N] words.` |
| Analyse data | `Here is [data]. Find [patterns/totals/outliers]. Show as [table/chart/file]. Explain in one sentence.` |
| Compare | `Compare [A] and [B] on [criteria] in a table, then recommend one for [situation].` |
| Learn | `Explain [topic] to someone who knows [background]. Use one analogy and one example.` |
| Check | `Review this for [errors/risks/gaps]. List issues by severity with a fix for each.` |
| Ground | `Using only the attached [source], answer [question]. Quote your evidence. Say NOT STATED if absent.` |
| Improve | `Shorter.` / `More direct.` / `You missed [X].` / `Now for a beginner.` |

## Question-first templates

| Situation | Say |
|---|---|
| Big or fuzzy task | `Before starting, interview me. Ask one batch of questions at a time, most important first. Don't start until I say "go".` |
| Might be unclear | `If anything important is unclear, ask up to 3 questions first; otherwise just answer.` |
| Check understanding | `Restate the task in your own words and list your assumptions before you begin.` |
| Turn answers into a brief | `Now write everything we agreed as a one-page spec: goal, requirements, out of scope, open questions, done-when.` |
| Claude Code feature | `Interview me in detail using the AskUserQuestion tool, then write SPEC.md.` then `/clear` and `Implement SPEC.md` |
| Fix a prompt | `Here's my prompt. What's ambiguous? Rewrite it to be clearer.` |
| Stress-test an answer | `What would a sceptical expert say is wrong with this? Then fix what matters.` |

## Claude Code cheat sheet

```text
claude                      start a session in the current folder
claude --permission-mode plan
claude --plugin-dir ./my-plugin
claude mcp add ...          add an MCP server
claude doctor               check the installation

/init      create CLAUDE.md          /memory    view memory files
/model     choose model              /effort    reasoning effort
/plan      plan without editing      /permissions  allow / ask / deny
/context   what is using context     /compact   summarise conversation
/clear     start fresh               /rewind    go back to a checkpoint
/mcp       MCP servers               /plugin    plugins
/agents    subagents                 /hooks     hooks
/schedule  cloud routines            /loop      repeat in this session
/ide       connect to your IDE       /usage     usage so far
/help      all commands

Shift+Tab  cycle permission modes    Esc        stop and redirect
Esc Esc    rewind menu (empty input) Ctrl+R     search history
@file      mention a file            !cmd       run a shell command
```

## Cost cheat sheet

| Lever | Saves | How |
|---|---|---|
| Right model | Biggest | Sonnet for everyday, Opus for hard, Haiku for bulk/simple subagents |
| Keep the cache | Up to ~90% of input | Pick model and effort at the start; don't switch mid-task |
| Small context | Every turn | `/clear` between tasks, short `CLAUDE.md`, fewer MCP servers and plugins |
| Lower effort | Output tokens | `/effort low` or `medium` for routine work |
| Short answers | Output tokens | Say the length you want |
| Subagents | Main context | Push logs, tests and searches into a subagent on a cheaper model |
| Batch API | 50% | For non-urgent API jobs |
| Measure | - | `/usage` (cost, cache hit rate, misses), `/context` (what fills the window) |

## File locations (Claude Code)

| What | Where |
|---|---|
| User memory | `~/.claude/CLAUDE.md` |
| Project memory | `./CLAUDE.md` or `./.claude/CLAUDE.md` |
| Local memory | `./CLAUDE.local.md` (gitignored) |
| Path rules | `.claude/rules/*.md` |
| Settings | `~/.claude/settings.json`, `.claude/settings.json`, `.claude/settings.local.json` |
| Skills | `~/.claude/skills/<name>/SKILL.md`, `.claude/skills/<name>/SKILL.md` |
| Subagents | `~/.claude/agents/<name>.md`, `.claude/agents/<name>.md` |
| Project MCP servers | `.mcp.json` |
| Plugin manifest | `<plugin>/.claude-plugin/plugin.json` |

## Habits that pay off

1. **Say who, what, why and what "done" means.**
2. **Name the output format** (table, `.xlsx`, artifact, 3 bullets).
3. **Iterate**: give feedback on the first draft.
4. **Use projects** for anything recurring.
5. **Ground factual answers** in a source, and ask for quotes.
6. **Check anything you could not spot being wrong.**
7. **Keep secrets and other people's personal data out.**
8. **Connect only what you need**; disconnect what you don't use.
9. **Plan before big code changes**, and review every diff.
10. **Turn repeated instructions into skills.**

## Official resources

- Help centre: [support.claude.com](https://support.claude.com)
- Claude Code docs: [code.claude.com/docs](https://code.claude.com/docs)
- Prompting guide: [platform.claude.com/docs](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/overview)
- Anthropic Academy (free courses): [anthropic.com/learn](https://www.anthropic.com/learn)
- Model Context Protocol: [modelcontextprotocol.io](https://modelcontextprotocol.io)

---
[Home](../README.md) | Previous: [Practice](17-practice.md)

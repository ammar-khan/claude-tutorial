# 10. Claude Code: Claude inside your repository

[Home](../README.md) | Previous: [Plugins](09-plugins.md) | Next: [IDE integration](11-ide-integration.md)

![Green code on a terminal screen](https://images.unsplash.com/photo-1608742213509-815b97c30b36?w=1200&q=80&auto=format&fit=crop)
<sub>Photo: Jake Walker on Unsplash</sub>

**Claude Code** is Claude working directly in a code repository. It reads
and edits real files, runs commands and tests, uses git, and shows you
diffs to review. Everything from earlier chapters still applies; this adds
a surface built for software work.

## Where it runs

| Surface | What it is | Best for |
|---|---|---|
| **Terminal (CLI)** | `claude` in any shell | The reference experience; scripting, servers, CI. |
| **Desktop app, Code tab** | A graphical app over the same engine | Visual diffs, several sessions side by side, preview, PR tracking. |
| **VS Code extension** | Native panel inside VS Code (and forks such as Cursor) | Staying in your editor. |
| **JetBrains plugin** | IntelliJ IDEA, PyCharm, WebStorm, GoLand and more | JetBrains users. |
| **Web** | [claude.ai/code](https://claude.ai/code) | Cloud sessions on GitHub repos, from any browser or phone. |

You need a paid Claude plan (Pro, Max, Team, Enterprise) or a Claude
Console (API) account. No API key is needed when you sign in with a plan.

## Install the CLI

Native installer (recommended; updates itself):

```bash
# macOS, Linux, WSL
curl -fsSL https://claude.ai/install.sh | bash
```

```powershell
# Windows PowerShell
irm https://claude.ai/install.ps1 | iex
```

Package managers (you update them yourself):

```bash
brew install --cask claude-code        # macOS Homebrew
winget install Anthropic.ClaudeCode    # Windows
npm install -g @anthropic-ai/claude-code   # needs Node.js 22+
```

> Security note: piping a script into your shell runs it with your
> permissions. Only do this with the official URL above, or prefer a
> package manager.

On Windows, install **Git for Windows** first; Claude Code uses Git Bash
for shell commands.

Check it worked:

```bash
claude --version
```

## Your first session, step by step

1. Open a terminal **in a project folder** (ideally a git repository you
   can safely revert):

   ```bash
   cd my-project
   claude
   ```

2. Sign in when your browser opens.
3. Trust the folder when asked. Claude Code can only work in this folder
   (plus any you add).
4. Ask for orientation first:
   `Give me a tour of this codebase: what it does, the main folders, how to run the tests.`
5. Create a project memory file: type `/init`. Claude writes a
   `CLAUDE.md` describing the project (see [chapter 13](13-claude-md.md)).
6. Make a small change **with a plan**: press `Shift+Tab` until the status
   bar shows plan mode, then ask
   `Add input validation to the signup form and a test for it.`
   Review the plan, then approve (see [chapter 12](12-plan-mode.md)).
7. Review the diff, run the tests, then ask Claude to commit on a new
   branch.

## Commands worth knowing

Type `/` to see them all.

| Command | What it does |
|---|---|
| `/init` | Generate a `CLAUDE.md` for this project. |
| `/model` | Choose the model (use aliases like `sonnet`, `opus`, `haiku`). |
| `/effort` | Set reasoning effort (low to max). |
| `/plan` | Plan the next request without editing anything. |
| `/permissions` | View and edit allow / ask / deny rules. |
| `/context` | See what is filling the context window. |
| `/clear` | Start fresh between unrelated tasks. |
| `/compact` | Summarise the conversation to free space. |
| `/rewind` | Go back to an earlier point (code and/or conversation). |
| `/memory` | Open CLAUDE.md files and auto memory. |
| `/mcp` | Manage MCP servers. |
| `/plugin` | Browse and manage plugins. |
| `/agents` | Manage subagents. |
| `/hooks` | See configured hooks. |
| `/schedule` | Create a cloud routine ([chapter 14](14-routines.md)). |
| `/loop` | Repeat a prompt on an interval in this session. |
| `/usage` | What this session has used. |
| `/doctor` | Diagnose installation problems. |
| `/ide` | Connect a terminal session to your IDE. |
| `/help` | Everything else. |

## Keyboard shortcuts

| Keys | Action |
|---|---|
| `Shift+Tab` | Cycle permission modes (Manual, accept edits, plan, auto...). |
| `Esc` | Stop Claude mid-turn so you can redirect it. |
| `Esc` `Esc` | With empty input: open the rewind menu. |
| `Ctrl+C` | Interrupt; press again on an empty prompt to exit. |
| `Ctrl+R` | Search previous prompts. |
| `Ctrl+O` | Show the detailed transcript. |
| `Ctrl+G` | Edit your prompt in your text editor. |
| `@` | Mention a file: `@src/app.ts` |
| `!` | Run a shell command directly: `!npm test` |

## Connect tools with MCP

```bash
# A hosted (HTTP) server, for you across all projects
claude mcp add --transport http --scope user docs https://example.com/mcp

# A local server started as a process, shared with the team via .mcp.json
claude mcp add --scope project playwright -- npx -y @playwright/mcp@latest

claude mcp list
```

Scopes: `local` (default: you, this project), `user` (you, all projects),
`project` (everyone, stored in `.mcp.json` at the repo root). Never put
secrets directly in `.mcp.json`; use environment variables.

## Subagents and hooks, briefly

- **Subagents** are specialist helpers with their own context window,
  tools and instructions, defined in `.claude/agents/<name>.md`. Claude
  delegates to them (for example a read-only "code-reviewer") so exploratory
  work does not clutter your main conversation. Manage with `/agents`.
- **Hooks** are shell commands that run automatically at lifecycle events,
  so something *always* happens instead of relying on Claude to remember.
  Example: format every file Claude edits.

  ```json
  {
    "hooks": {
      "PostToolUse": [
        {
          "matcher": "Edit|Write",
          "hooks": [
            {
              "type": "command",
              "command": "jq -r '.tool_input.file_path' | xargs npx prettier --write"
            }
          ]
        }
      ]
    }
  }
  ```

  Put it in `.claude/settings.json` (team) or `~/.claude/settings.json`
  (you). Other events include `PreToolUse`, `Notification`,
  `UserPromptSubmit`, `Stop` and `SessionStart`.

## Working efficiently

- **Give it a way to check its work.** Tests, a linter or a build command
  in `CLAUDE.md` let Claude verify changes instead of guessing.
- **One task per session.** Start new work with `/clear`; unrelated
  history dilutes attention and uses up context.
- **Settle on a model early.** Claude Code caches the start of the
  conversation; changing model mid-session means that cache is rebuilt.
- **Roll back rather than patch.** If an approach goes wrong, `/rewind` to
  before it and describe what you want differently.
- **Keep always-loaded context lean.** Short `CLAUDE.md`, detail in
  skills, and only the plugins and MCP servers you use.
- **Commit on a branch** after each working step, so every change is easy
  to review and revert.

## Troubleshooting

| Problem | What to check |
|---|---|
| `claude: command not found` | Open a new terminal so PATH refreshes; on Windows check Git for Windows is installed; run `claude doctor`. |
| Login loops or fails | Run `/login` again; unset `ANTHROPIC_API_KEY` if you meant to use your plan. |
| Quality drops in a long session | Check `/context`; use `/compact` to summarise or `/clear` to start fresh. |
| Unexpected edits | Check the mode in the status bar; restore with `/rewind` or `git restore`. |
| Too many permission prompts | Add allow rules for safe, frequent commands with `/permissions`. |
| MCP server not working | `/mcp` shows status and lets you re-authenticate; `claude mcp list` from the shell. |

Docs: [code.claude.com/docs](https://code.claude.com/docs). You can also
just ask Claude Code how to use Claude Code.

---
[Home](../README.md) | Previous: [Plugins](09-plugins.md) | Next: [IDE integration](11-ide-integration.md)

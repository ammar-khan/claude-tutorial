# 11. IDE integration: VS Code, JetBrains (IntelliJ) and Visual Studio

[Home](../README.md) | Previous: [Claude Code](10-claude-code.md) | Next: [Plan mode and permissions](12-plan-mode.md)

![Code editor showing source code](https://images.unsplash.com/photo-1619410283995-43d9134e7656?w=1200&q=80&auto=format&fit=crop)
<sub>Photo: Juanjo Jaramillo on Unsplash</sub>

Claude Code works in any terminal, but inside your editor you also get
visual diffs, your current selection as context, and one-key file
references.

| Editor | Official integration | How it connects |
|---|---|---|
| VS Code (and forks like Cursor) | Yes: **Claude Code** extension | Native graphical panel |
| JetBrains (IntelliJ IDEA, PyCharm, WebStorm, GoLand, PhpStorm, Android Studio) | Yes: **Claude Code [Beta]** plugin | Runs the CLI in the IDE terminal and connects to it |
| Visual Studio 2022 / 2026 | No official extension (as of Sep 2026) | Run the CLI in Visual Studio's terminal |

---

## VS Code

### Install

1. Requirements: VS Code 1.94 or newer and a paid Claude plan or Console
   account.
2. Press `Ctrl+Shift+X` (Windows/Linux) or `Cmd+Shift+X` (Mac) to open
   **Extensions**.
3. Search **Claude Code**, check the publisher is **Anthropic**, and click
   **Install**.
4. Forks such as Cursor can install the same extension (or get it from the
   Open VSX registry).

### Open Claude

- Click the **Spark** icon in the editor toolbar (top right; appears when
  a file is open), or
- Click the Spark icon in the **Activity Bar** (left) to see your sessions,
  or
- `Ctrl+Shift+P` / `Cmd+Shift+P` > type **Claude Code** > **Open in New Tab**.

Sign in the first time it opens.

### Everyday use, step by step

1. **Select some code.** Claude sees your selection automatically; the
   prompt footer shows how many lines.
2. Press `Alt+K` (Win/Linux) / `Option+K` (Mac) to insert a precise
   reference such as `@app.ts#5-10`.
3. Pick the **mode** in the prompt box (Manual, plan, accept edits, auto).
4. Ask: `Explain this function and suggest a safer version.`
5. Claude's edits appear as **inline diffs**. Accept or reject them, all at
   once or change by change (also available from the right-click menu).
6. Plans open as a document you can **comment on** before approving.
7. Open extra conversations in new tabs for side tasks. A blue dot on the
   Spark icon means a permission request is waiting; orange means it
   finished in the background.

| Shortcut (Win/Linux) | Mac | Action |
|---|---|---|
| `Ctrl+Esc` | `Cmd+Esc` | Toggle focus between editor and Claude |
| `Ctrl+Shift+Esc` | `Cmd+Shift+Esc` | New conversation in a tab |
| `Alt+K` | `Option+K` | Insert @-mention of file and selection |

The extension and the CLI share settings, `CLAUDE.md` files, skills and
plugins. You can also still run `claude` in VS Code's integrated terminal.

---

## JetBrains: IntelliJ IDEA, PyCharm, WebStorm and friends

### Install

1. **Install the CLI first** ([chapter 10](10-claude-code.md)). The plugin
   does not bundle it.
2. In the IDE: **Settings > Plugins > Marketplace**, search **Claude Code**
   (published by Anthropic, marked Beta), install, and **restart** the IDE.

### Use it

1. Open your project, then press `Ctrl+Esc` (Win/Linux) / `Cmd+Esc` (Mac)
   or click the **Claude Code** button. This runs `claude` in the IDE
   terminal and connects automatically.
2. Your current selection or open tab is shared with Claude.
3. `Alt+Ctrl+K` (Win/Linux) / `Cmd+Option+K` (Mac) inserts a file reference
   like `@src/auth.ts#L1-99`.
4. Proposed changes open in the IDE's **diff viewer**. (Switch with the
   **Diff tool** setting in `/config`.)
5. Claude can read the IDE's inspection **diagnostics** (lint and syntax
   errors) when you ask it to.
6. Switch permission modes with `Shift+Tab`, as in the terminal.

Started `claude` in an external terminal? Run `/ide` to connect it to the
running IDE.

### Settings and gotchas

- **Settings > Tools > Claude Code [Beta]**: set a custom Claude command
  (for WSL: `wsl -d Ubuntu -- bash -lic "claude"`).
- **Esc does not interrupt Claude?** Settings > Tools > Terminal: untick
  "Move focus to the editor with Escape".
- **Remote Development:** install the plugin on the **remote host**.
- **Security:** in accept-edits or auto mode, Claude could edit IDE config
  files that the IDE runs automatically. Prefer Manual mode for sensitive
  projects.

---

## Visual Studio (2022 / 2026)

There is no official Anthropic extension for Visual Studio at the time of
writing. The supported approach is to run the CLI inside Visual Studio.

### Step by step

1. Install the CLI and **Git for Windows** ([chapter 10](10-claude-code.md)).
2. Open your solution in Visual Studio.
3. Open **View > Terminal** (a Developer PowerShell pane). Make sure it is in
   the folder that contains your `.sln` (usually the repo root).
4. Run `claude`. Everything in chapters 10, 12 and 13 now applies.
5. Useful prompts for .NET work:
   - `Build the solution with dotnet build and fix any errors.`
   - `Add xUnit tests for OrderService.CalculateTotal, then run dotnet test.`
   - `Explain what this project's Program.cs sets up.`
6. Visual Studio notices files changed on disk and reloads them. Review
   changes with **Git Changes** (View > Git Changes) before committing.

### Tips

- Add a `CLAUDE.md` describing how to build and test the solution (for
  example `dotnet build MySolution.sln`, `dotnet test`), and anything
  Claude should never touch (generated code, migrations).
- For graphical diffs and inline review, you can open the same folder in VS
  Code with the Claude Code extension at the same time.
- Community-made Visual Studio extensions exist that wrap the CLI. They are
  **not** made or endorsed by Anthropic. Review their source and
  permissions before installing.

---
[Home](../README.md) | Previous: [Claude Code](10-claude-code.md) | Next: [Plan mode and permissions](12-plan-mode.md)

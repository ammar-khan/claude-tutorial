# 9. Plugins: install a whole toolkit

[Home](../README.md) | Previous: [Skills](08-skills.md) | Next: [Claude Code](10-claude-code.md)

![Cogs and gears](https://images.unsplash.com/photo-1593062037896-764e9f52029e?w=1200&q=80&auto=format&fit=crop)
<sub>Photo: Tim Mossholder on Unsplash</sub>

A **plugin** packages several pieces into one installable unit:

- **Skills** - procedures Claude follows
- **Connectors / MCP servers** - apps Claude can reach
- **Subagents** - specialist helpers Claude can delegate to
- **Hooks** - commands that run automatically at certain moments
- **Commands** - slash commands (now part of skills)

Instead of setting up five things by hand, you install one plugin, for
example "sales toolkit" or "code review kit", and get them all.

Plugins are published in **marketplaces**: catalogues (often a GitHub
repository) that list plugins and where to fetch them.

## Plugins in the Claude app and Cowork (paid plans)

1. Go to **Customize > Plugins** (tab) > **Discover**.
2. Pick a plugin and click **Install** (or **Add**).
3. Approve any connectors it wants to use and sign in to those apps.
4. Use it: its skills and commands are now available in chat and Cowork.

To add another marketplace: **Personal plugins > + > Add marketplace**,
then choose a listed marketplace or paste a GitHub repository.

Note: hooks and subagents only run in Cowork and Claude Code; in plain
chat you get the skills and connectors.

## Plugins in Claude Code

```text
/plugin                                         open the plugin manager
/plugin marketplace add owner/repo              add a marketplace from GitHub
/plugin install commit-commands@claude-plugins-official
```

The `/plugin` manager has tabs:

- **Discover** - browse plugins, including a **context cost** estimate for
  plugins from Anthropic's official marketplace.
- **Installed** - enable, disable or remove plugins. The **Not used
  recently** group shows ones you could turn off.
- **Marketplaces** - add or remove catalogues.

Anthropic's official marketplace (`claude-plugins-official`) is added
automatically the first time you start an interactive session.

**Install scopes:** *user* (you, every project), *project* (everyone in
the repo, via the committed `.claude/settings.json`), or *local* (you,
this repo only).

## Build your own plugin

A plugin is just a folder:

```text
my-plugin/
  .claude-plugin/
    plugin.json          name, version, description
  skills/
    review/SKILL.md      becomes /my-plugin:review
  agents/
    reviewer.md          a subagent
  hooks/
    hooks.json           lifecycle hooks
  .mcp.json              MCP servers
```

Minimal `plugin.json`:

```json
{
  "name": "my-plugin",
  "version": "1.0.0",
  "description": "My personal writing and review helpers"
}
```

Try it without a marketplace:

```bash
claude --plugin-dir ./my-plugin
```

To share it, put it in a Git repository with a
`.claude-plugin/marketplace.json` listing your plugins; others add it with
`/plugin marketplace add`. Guide:
[code.claude.com/docs/en/plugins/create](https://code.claude.com/docs/en/plugins/create).

## Before you install anything

- **A plugin runs as you.** Its hooks and MCP servers can run code with
  your permissions. Install only from sources you trust and skim what it
  contains.
- **Every enabled plugin costs context.** Each skill's name and
  description sits in Claude's context on every turn. Disable plugins you
  are not using.
- Prefer plugins with a clear maintainer, a changelog, and a licence.

---
[Home](../README.md) | Previous: [Skills](08-skills.md) | Next: [Claude Code](10-claude-code.md)

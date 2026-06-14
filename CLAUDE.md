# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Directory Is

`~/.claude` is the Claude Code global configuration directory. Sessions launched without a project-specific working directory run here. It is not a software project — there is no build system or test runner.

## Configuration

**`settings.json`** — Global Claude Code settings. Current config: dark theme, `claude-mem@thedotmack` plugin enabled.

To change settings, edit `settings.json` directly or use `/config` in Claude Code.

## Installed Plugins

### claude-mem (v13.6.0) — `thedotmack` marketplace

A persistent memory system that compresses session context across conversations. Installed at `plugins/marketplaces/thedotmack/`.

**How it hooks into Claude Code:**
- `Setup` — version check on startup
- `SessionStart` — starts the worker service and injects prior session context
- `UserPromptSubmit` — session-init (loads relevant memories)
- `PreToolUse` (Read) — injects file-level context before reads
- `PostToolUse` (all) — records observations after every tool call
- `Stop` — summarizes the session into compressed memory

**Memory database**: `~/.claude-mem/claude-mem.db` (SQLite + Chroma vector store at `~/.claude-mem/chroma/`)

**Key skills available** (invoke with `/skill-name`):
- `mem-search` — search past session memory
- `make-plan` / `do` — plan then execute multi-step tasks
- `learn-codebase` — prime a project by reading all source files
- `timeline-report` — generate a narrative of a project's development history

**Plugin management:**
```bash
/plugin install <name>@<marketplace>   # install a plugin
/plugin > Discover                     # browse marketplace
```

## Plugin Marketplaces

Two marketplaces are registered under `plugins/marketplaces/`:
- **`thedotmack`** — claude-mem and related plugins by Alex Newman
- **`claude-plugins-official`** — Anthropic's curated directory (`/plugins` = internal, `/external_plugins` = third-party)

## File-Based Memory

`projects/C--Users-thiag--claude/memory/` holds persistent memories written by Claude in sessions run from this directory. Memories are organized by type (`user`, `feedback`, `project`, `reference`) with a `MEMORY.md` index file. Read `MEMORY.md` first when resuming work to recover prior context.

## Plugin Structure Reference

Each plugin follows:
```
plugin-name/
├── .claude-plugin/plugin.json   # metadata
├── .mcp.json                    # MCP server config (optional)
├── hooks/hooks.json             # lifecycle hooks (optional)
├── skills/                      # SKILL.md files
└── commands/                    # slash command definitions
```

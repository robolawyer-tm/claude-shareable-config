# Claude Code — Shared Configuration

Shared Claude Code config for all projects under `~/repos/`.

## Structure

```
.claude/
  settings.json       # shared permissions and hooks
  commands/           # slash commands available across all projects
  README.md           # this file
```

## Usage

Clone into `~/repos/.claude/` to apply shared settings and commands to all subdirectory projects.

## Layers

| Layer | Path | Scope |
|---|---|---|
| Global | `~/.claude/` | Everything |
| Shared | `~/repos/.claude/` | All repos |
| Project | `~/repos/<project>/.claude/` | One project |

---

*Scaffolded with [Claude Code](https://claude.ai/code)*

---
name: publish-config
description: Publish whitelisted files from ~/.claude to ~/repos/claude-shareable-config and push to GitHub. Shows a diff and asks for confirmation before committing.
---

You are executing the publish-config skill. Sync whitelisted files from `~/.claude/` to `~/repos/claude-shareable-config/`, show what changed, and ask the user before pushing.

## Whitelist

Copy these files/dirs from `~/.claude/` to `~/repos/claude-shareable-config/`:

- `CLAUDE.md`
- `settings.json`
- `commands/` (full directory)
- `skills/` (full directory)

## Steps

1. For each whitelisted file, copy it to `~/repos/claude-shareable-config/`.
2. For each whitelisted directory, use `rsync -a --delete` to sync it.
3. Run `git -C ~/repos/claude-shareable-config diff --stat` and show the output to the user.
4. Ask: "Push to GitHub? [y/N]"
5. If yes: `git -C ~/repos/claude-shareable-config add -A`, commit with message `Publish from ~/.claude — YYYY-MM-DD`, push.
6. If no: confirm "Aborted — nothing committed."

## After pushing

Confirm in one line: `Published to claude-shareable-config — YYYY-MM-DD`

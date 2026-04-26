# CLAUDE.md — Shared / robolawyer-tm

> Applies to all projects under `~/repos/`. Project-specific CLAUDE.md files extend this.

---

## Non-negotiables

1. Local-first — zero cloud dependencies
2. Privacy-preserving — all data stays local, SSH tunnels for transport
3. No external taxonomies — all structure emerges from the data
4. Analogical orientation — output serves human emotion and empathy
5. Filesystem transparency — no opaque formats, human-readable JSON
6. Python 3 + shell-first
7. Structure first — define target file layout before writing any process code

---

## Code style

- **Shell-first** at the high level — keep processes visible as shell commands
- **Python** for executables and libraries — scripts easily wrapped into shell commands
- **pipx** for wrapping Python code as shell-accessible commands
- No opaque formats. No external taxonomies. All structure emerges from data.
- **Naming convention**: hyphens for project/repo names (`vivify-inferences`, `star-bridge`), underscores for files, directories, and executables (`vivify_core.py`, `extract_keywords`, `inferences/`)
- **Python — app-level (public-facing)**: Standard module structure, FABRIC component names as module names, every module standalone via `if __name__ == '__main__':`. No pipx. Readable by anyone.
- **Python — housekeeping (local admin)**: pipx-wrapped via a shell script in `sys_adm/`. Not for public repos.
- **STDIN**: All housekeeping executables accept data on standard input. Python uses `fileinput.input()`. Shell uses pipe-detect: `if [ -p /dev/stdin ]; then while IFS= read -r line; do ...; done; fi`
- Shell scripts use the appropriate template from `~/repos/sys_adm/`:
  - `shell_template` — general scripts (header, `usage()`, `realpath`, `items[]` loop)
  - `shell_template_exec` — library/executable hybrids (`parse_args()`, `process_item()`, `main()`, `BASH_SOURCE` guard, sourceable)
  - `shell_template_pipx` — thin wrappers delegating to a pipx-installed Python command

---

## Documentation standard

All documentation follows a single defining sentence followed by 3–6 supporting bullets that expand without repetition. Full schema: `pillars/doc_standard_v1.json`

- Defining sentence: one direct claim, active voice, 25 words max, no vague qualifiers
- Bullets: each expands a distinct angle — evidence, example, or constraint — 15 words avg
- Forbidden: multiple claim sentences, bullets that restate the opener, nested bullets, concluding statements in exploratory sections

---

## LLM signing standard

Every LLM-edited file gets a footer line recording the model, date, path, and change.

- Format: `# llm: model-id | YYYY-MM-DD | full/path/from/repos | what changed`
- Use `<!-- llm: ... -->` for HTML/markdown files
- Full path from `~/repos/` — never filename alone
- One line per edit session at the bottom of the file
- A scan script can aggregate all footers across the codebase on demand

---

## Housekeeping rules

- **Before editing any existing file**, back it up first: `backit ~/repos/<project>/<file>`
- Backups mirror path structure under `~/backups/` — outside all repos, safe from git commands
- AI must not run destructive git commands (`reset`, `clean`, `checkout .`, `force-push`) without explicit user confirmation
- **Never delete or overwrite any script or file** without explicit user confirmation — run `backit` first, then ask
- New shell scripts start from `~/repos/sys_adm/shell_template`
- `sys_adm` repo is the source for scripts deployed to `~/bin`

---

<!-- llm: claude-sonnet-4-6 | 2026-04-26 | repos/.claude/CLAUDE.md | created shared config layer extracted from pillars/CLAUDE.md -->

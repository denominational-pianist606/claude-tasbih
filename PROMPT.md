# Install prompt

Paste this into Claude Code (running in this repo) to have it installed for you:

---

Read `spinner-verbs.json` in this repo and merge its top-level `spinnerVerbs` key into
my Claude Code user settings at `~/.claude/settings.json` (on Windows:
`C:\Users\<me>\.claude\settings.json`).

Requirements:
- Preserve every existing key in my settings file — do not drop or reorder my current
  settings.
- If a `spinnerVerbs` key already exists, replace it wholesale with the one from
  `spinner-verbs.json`.
- Keep the result valid JSON (correct commas, UTF-8 without BOM) and verify by parsing
  it after writing.
- Show me a short diff of what changed, then tell me to restart Claude Code so the new
  spinner verbs take effect.

---

## Variants

**Append instead of replace** (keep Claude's built-in verbs too): after merging, set
`spinnerVerbs.mode` to `"append"`.

**Project-only install:** merge into `.claude/settings.json` in the current project
instead of my user settings.

**Uninstall:** remove the `spinnerVerbs` key from my Claude Code settings, keep every
other key intact, verify the file still parses, and remind me to restart.

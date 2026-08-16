# claude-tasbih

Replace Claude Code's random spinner verbs ("Cogitating…", "Noodling…") with dhikr —
the tasbih phrases and the 99 Names of Allah (Asma-ul-Husna).

Every time Claude Code is thinking, you see something like:

```
✳ SubhanAllah — Glory be to Allah… (12s · ↑ 1.4k tokens · esc to interrupt)
✳ Al-Fattah — The Opener… (4s · ↑ 320 tokens · esc to interrupt)
```

## What's in here

| File | Purpose |
|---|---|
| `spinner-verbs.json` | The `spinnerVerbs` block to merge into your Claude Code settings |
| `README.md` | This file |
| `PROMPT.md` | A ready-to-paste prompt so Claude Code installs it for you |

## Install

### Option A — let Claude Code do it

Open Claude Code in this folder and paste the contents of [`PROMPT.md`](PROMPT.md).

### Option B — manual

1. Open your user settings file:
   - Windows: `C:\Users\<you>\.claude\settings.json`
   - macOS / Linux: `~/.claude/settings.json`
2. Copy the `"spinnerVerbs": { ... }` object from `spinner-verbs.json` and merge it
   in as a **top-level key**, alongside your existing keys.
3. Mind the commas — the file must stay valid JSON. Example result:

```json
{
  "model": "opus[1m]",
  "tui": "fullscreen",
  "spinnerVerbs": {
    "mode": "replace",
    "verbs": ["SubhanAllah — Glory be to Allah", "..."]
  }
}
```

4. Restart Claude Code (`/exit`, then relaunch). The spinner picks a random verb per turn.

## Settings reference

- `mode`
  - `"replace"` — use **only** these verbs (default here)
  - `"append"` — add these on top of Claude Code's built-in verbs
- `verbs` — array of strings. 104 entries here: 5 core dhikr phrases followed by the
  99 Names with English meanings.

Settings precedence, if you want it scoped differently:

| File | Scope |
|---|---|
| `~/.claude/settings.json` | You, everywhere (recommended) |
| `<project>/.claude/settings.json` | One project, shared via git |
| `<project>/.claude/settings.local.json` | One project, just you (gitignored) |

## Customising

Edit the `verbs` array freely — add salawat, du'a, or ayah fragments. Keep each line
short (roughly under 45 characters) so it doesn't wrap in a narrow terminal.

To go back to the defaults, delete the `spinnerVerbs` key and restart.

## Notes

- Transliterations use a simple Latin scheme without diacritics for terminal safety.
- The em dash separator (`—`) and apostrophes are plain UTF-8; save the settings file
  as UTF-8 (no BOM) if you edit it by hand on Windows.
- Purely cosmetic — no effect on Claude Code's behaviour, permissions, or billing.

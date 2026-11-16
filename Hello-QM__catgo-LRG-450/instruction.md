# Issue

**Title:** feat(terminal): Ctrl+click a directory navigates the Files panel

## Description

## What

In CatGo's embedded terminal, Ctrl+click on a **file** path already opens it in the viewer/editor. Ctrl+click on a **directory** now moves the **Files panel** to that directory instead of trying to open it as a file.

## How

Reuses the existing **Directory-Sync** infrastructure rather than building a new channel:

- The click dispatches the same `catgo-terminal-cwd` window event the OSC7 `sync_cwd` path already emits, so the listener in `desktop/sidebar/cwd-sync.svelte.ts` navigates the active Files panel — **Local Files** for a local terminal, the matching **SSH session** for a remote one.
- It fires **regardless of the `sync_cwd` toggle** — a Ctrl+click is an explicit jump, not passive CWD following.

Dir-vs-file detection is async (can't run inside xterm's synchronous link `activate()`):

| Terminal | Detection | dir = |
|---|---|---|
| local (no session_id) | `GET /workflow/files/browse?dir=…` | `200` (404 = file) |
| remote (SSH) | `listFiles(session_id, path)` | `success` |

Any error falls back to opening the path as a file — the prior behaviour.

The dir-vs-file branch is split into `src/lib/structure/terminal-path-nav.ts` so it is unit-testable without a DOM/xterm harness; `TerminalPanel.svelte`'s link `activate()` just calls into it.

## Tests

- **+4 vitest** (`src/lib/structure/__tests__/terminal-path-nav.test.ts`): directory → navigate, file → open, remote `session_id` forwarded, detection-failure → safe file fallback. All pass.
- `svelte-check` clean on the changed files (the repo's 13 pre-existing errors are unrelated).

## Notes

- Same-window only by design (mirrors the existing CWD-sync: a popped-out terminal must not move the origin window's files — no cross-window BroadcastChannel).
- No change to the file-click path; only directories take the new branch.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `877ab48b2a59`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
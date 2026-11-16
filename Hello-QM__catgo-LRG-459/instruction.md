# Issue

**Title:** fix(desktop): reuse popout updates via the DOM storage event

## Description

## Symptom

/#458: Window + **Overwrite** — the first structure opens in the popout, but opening another file changes nothing.

## Root cause — both delivery paths broken independently

- **Browser named-window path**: the reuse URL is byte-identical every time (`#structure?key=catgo-popout-reuse`), so `window.open(url, name)` performs no navigation — the popout never re-reads the payload.
- **Tauri path**: depends on `getByLabel` + event delivery working end-to-end, with no fallback when it doesn't.

## Fix

Third channel that needs neither IPC nor navigation: the popout listens for the **DOM `storage` event** on the reuse key. localStorage writes fire it in every *other* same-origin window — exactly the semantics needed (the writer never notifies itself). The Tauri event stays as belt-and-braces; whichever channel fires first consumes the payload (`removeItem`), the loser reads null and no-ops.

## Verification

**Live-verified** at :3100: main window opens Fe-BCC with Window+Overwrite → the existing popout switches BaTiO₃→Fe with no navigation (URL unchanged). Payload-consumption logic covered by the #458 vitest suite (4 pass).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9c7074ee35c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
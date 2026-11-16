# Issue

**Title:** fix(view): catgo view always replaces the External pane (ase-gui semantics)

## Description

## Problem

`catgo view <file>` (and `catgo push`) only worked **once**. After the first push, every later push to the External pane was silently dropped — the pane stayed frozen on the first structure.

## Root cause

The CLI pushes via `POST /api/view/upload-and-load`, which the backend tagged with `intent="load"`. The frontend load-gate (`should_apply_push` in `tool-handler.ts`) **holds — and the SSE handler then drops** any `load` push once the pane already shows a structure:

```js
return !(intent === 'load' && (viewer_has_structure || had_structure_backend))
```

`view_state.push_structure` self-computes `had_structure = bool(panel_structures.get(pid))`, which is `True` from the 2nd push on → every repeat push is dropped.

That hold exists so CatBot loading *autonomously* into a user's working tab prompts before clobbering. But an explicit `catgo view` is the user asking to **show this structure now** — like `ase gui` — and the External pane (`panel_id="default"`) is the dedicated external-push target, so replacing is its whole purpose.

## Fix (backend + CLI only — no frontend change)

The gate already always applies `intent="edit"`, so:

- `upload-and-load` gains an `intent` query param, **default `"load"`** so the CatBot load-into-occupied-tab prompt and existing tests are unchanged.
- the `catgo view` / `catgo push` CLI now sends `intent=edit`, so repeated pushes always apply and the External pane shows the latest structure.

## Verification

- **Live e2e**: two sequential pushes to `panel=default` now emit `intent="edit"` with `had_structure` false then true → the gate applies both (B replaces A) instead of dropping the second.
- **Tests**: +2 (backend route honours the `intent` param; CLI sends `intent=edit`). **225 passed** across `server/tests/cli` + view/push/intent suites.

> Note: only affects the single-structure path; `push_trajectory` is untouched. The desktop app's bundled backend ships this on the next release; until then the `catgo view`-autostarted (editable) backend carries the fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `877ab48b2a59`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** fix(desktop): CatBot pane Close/Popout buttons work

## Description

The standalone CatBot pane's **Close** and **Popout** buttons were unresponsive (found while testing CatBot in the desktop app).

1. **Close** — Close/Popout reset the pane via `Object.assign(pane, create_empty_pane())`, but `create_empty_pane()` omitted `initial_panel`. `Object.assign` only copies keys present in the source, so the existing `initial_panel: 'chat'` survived → the chat branch kept rendering → the click fired but nothing changed. Fix: `create_empty_pane()` returns `initial_panel: undefined`. Verified live (Chrome): Close → landing page.

2. **Popout** — used plain `window.open`, which doesn't create a window in a Tauri WebView (silently dead in the packaged app). Now tries the Tauri `WebviewWindow` API first (window.open fallback for the browser), mirroring `Structure.svelte`'s `popout_chat`, and tags the URL with `tab_id`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ac0cafe8c8f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
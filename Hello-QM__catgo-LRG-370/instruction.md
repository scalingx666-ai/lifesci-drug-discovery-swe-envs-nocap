# Issue

**Title:** feat(chat): CatBot loads a structure → offer Split-view / New-window

## Description

**Problem:** a standalone CatBot chat pane has no 3D viewer, so a structure CatBot loads (pushed to the backend panel) is invisible — CatBot says "已显示在视图中" but the user sees nothing.

**Behaviour:** on every structure load, ChatPane shows a non-blocking inline card:
> 📦 Loaded **<formula>** (n) — [ ⊟ Split view ] [ ⧉ New window ]

- **Split view** — splits the chat leaf into left = 3D viewer (pulls the structure from `/view/structure/current` and renders it) + right = the chat (history kept, keyed by tab id).
- **New window** — opens the panel's structure in a separate window (`open_structure_in_new_window` → Tauri WebviewWindow / window.open).

**How:** ChatPane subscribes to `GET /view/subscribe?panel_id` (`structure` events only, deduped by formula+atom-count) and surfaces the card. Handlers wired only on the standalone chat pane (`desktop/App.svelte`); docked chat and the popout pass no handlers → unchanged. Spec: `docs/superpowers/specs/2026-06-17-catbot-load-structure-view-prompt-design.md`.

**Verified live** (chrome-devtools on :3100): push TiO2 → card appears → Split view → left viewer renders TiO2 (Ti/O atoms + bonds), right chat kept. en/zh i18n in parity.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `449a48cba3ea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
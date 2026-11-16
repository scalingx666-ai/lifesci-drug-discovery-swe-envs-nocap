# Issue

**Title:** fix(desktop): only the reuse popout listens for the reuse payload

## Description

## Symptom

: Window + Overwrite — the popout opens but shows the **landing page** instead of the structure (when other structure popouts are open).

## Root cause

#459's listeners were registered by **every** `#structure` popout, including Window+New ones. Payload delivery is consume-once (`removeItem`): an already-open popout's storage listener fired instantly and ate the reuse payload while the freshly created reuse window was still booting — its boot-time read then got null → landing page.

## Fix

Gate both channels (DOM storage event + Tauri event) on the popout's **own hash key** being `catgo-popout-reuse`. Only the reuse window consumes reuse payloads; Window+New popouts (unique keys) never listen.

## Verification

**Live-verified** at :3100 with a Window+New popout (BaTiO₃) open: Window+Overwrite open renders Fe in the reuse popout — not stolen, no landing page — and the New popout keeps BaTiO₃. Overwrite updates continue to work (#459 scenario re-checked).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a2a24366096`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
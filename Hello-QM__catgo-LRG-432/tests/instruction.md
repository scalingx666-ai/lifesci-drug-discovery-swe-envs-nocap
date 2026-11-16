# Issue

**Title:** fix(web): embed "Get the App" pill in landing instead of floating over editor

## Description

## Summary

The STATIC_ONLY web build's **下载客户端 / Get the App** badge was a `position: fixed` `GetAppButton` mounted at app root, so it floated over **every** view — including the structure editor after a structure was loaded (see screenshot in issue: pill hovering bottom-right of the editor).

## What changed

- Removed the root-level `<GetAppButton />` (the fixed floater).
- Added the download pill **inside the landing block** as an absolutely-positioned corner pill (bottom-right), mirroring the existing **Star on GitHub** (top-right) and **lab-link** (top-left) pills. Landing-only by construction, still gated on `STATIC_ONLY`.
- Deleted the now-dead `GetAppButton.svelte` component and its `src/lib/index.ts` export.

## Why

The pill should behave like Star-on-GitHub — embedded in the landing page, gone once you enter the editor — not a persistent floating overlay.

## Validation

- Ran the STATIC_ONLY web build (`VITE_STATIC_ONLY=true pnpm desktop:dev`) and verified in-browser:
  - Landing: pill embedded bottom-right alongside the GitHub/lab pills.
  - After loading a structure: **no** floating download button over the editor.
  - JS check: zero `position:fixed` download floaters remain.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b0760bed51c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
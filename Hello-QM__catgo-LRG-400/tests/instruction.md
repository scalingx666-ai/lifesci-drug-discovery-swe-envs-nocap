# Issue

**Title:** fix(hpc): bind fetch to globalThis in managed downloads (WebKitGTK)

## Description

HPC file downloads failed in packaged Linux/Tauri builds with `Can only call Window.fetch on instances of Window`. `hpc-download.ts` stored a bare `fetch` (`fetch_impl: fetch`) and called it as `deps.fetch_impl(...)` → `this === deps`. WebKitGTK enforces a Window receiver for fetch (Chromium/dev does not — so it only bit the installed app). Bind to globalThis.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca53d1fbef94`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
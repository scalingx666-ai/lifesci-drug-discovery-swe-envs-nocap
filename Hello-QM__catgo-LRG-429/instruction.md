# Issue

**Title:** fix(release): Windows NSIS PATH (no EnVar) + macOS team-id secret

## Description

Hotfix for the v1.4.0 desktop build (the tag build failed on Windows + macOS; this commit is already on the `v1.4.0` tag and rebuilding — this PR lands it on `main`).

- **Windows**: `EnVar::SetHKCU` aborted makensis — Tauri's bundled NSIS ships no EnVar plugin. Rewrote the PATH append with **core NSIS only** (HKCU `Environment` registry write + `WM_SETTINGCHANGE` broadcast).
- **macOS**: notarization failed *"Team ID must be at least 3 characters"* — the env read a nonexistent `APPLE_TEAM_ID` secret. Now points `APPLE_TEAM_ID` at the existing **`APPLE_DEVELOPMENT_TEAM`** secret (the one the iOS workflow already uses). Signing itself was already working.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b719e712e9da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
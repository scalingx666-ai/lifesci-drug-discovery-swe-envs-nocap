# Issue

**Title:** chore(release): v1.4.1

## Description

Version bump to **1.4.1** across desktop surfaces + refreshed release notes.

**Highlights**: in-app auto-update (Win/macOS one-click, Linux notify) · signed & notarized macOS · bonds preserved when adding a lattice · Search-Database OPTIMADE cold-start fix · VS Code trajectory perf + plot axis-label fixes · iOS App Store build.

Surfaces bumped: `package.json`, `src-tauri/tauri.conf.json`, `src-tauri/Cargo.toml` (+lock), `deploy/download/index.html`. Updated `tauri-build.yml` releaseBody (macOS now signed; New-in-1.4.1) + `CHANGELOG.md`. Tagging `v1.4.1` after merge triggers the signed/notarized/auto-update desktop build.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0233e18b8ab4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
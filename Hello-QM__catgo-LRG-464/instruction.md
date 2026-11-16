# Issue

**Title:** chore(release): v1.4.2

## Description

Version bump + release notes for **v1.4.2** — the fix batch from the 2026-07-01/02 testing round (#448–#463).

Surfaces bumped (mirrors #444): `package.json`, `src-tauri/tauri.conf.json`, `src-tauri/Cargo.toml` + `Cargo.lock`, `deploy/download/index.html` VERSION, `CHANGELOG.md` (new 1.4.2 section), `tauri-build.yml` releaseBody (New in 1.4.2; 1.4.0 section rotated out).

After merge: tag `v1.4.2` → tauri-build (Win/macOS/Linux + updater `latest.json`) + vscode sidecars run on the tag; draft release gets published once builds are green.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b6927a216254`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
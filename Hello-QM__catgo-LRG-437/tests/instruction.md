# Issue

**Title:** fix(build): pin @tauri-apps/plugin-updater to 2.9.x (match Rust crate)

## Description

iOS build failed: `Found version mismatched Tauri packages` — npm `@tauri-apps/plugin-updater@2.10.1` vs Rust `tauri-plugin-updater@2.9.0` (latest on crates.io). Tauri CLI requires matching major/minor per plugin. Pin npm to `~2.9.0`. Also unblocks desktop `tauri-build` (same check).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `afb51ba81a74`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
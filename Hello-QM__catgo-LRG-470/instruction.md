# Issue

**Title:** chore(release): v1.4.3

## Description

Version bump + release notes for **v1.4.3** — the #465–#469 fix batch (LAMMPS `.data` open chain, PBC image-search perf, terminal CJK synthetic-DEL swallowing, doc-viewer Render toggle), all user-verified in dev.

Surfaces bumped (mirrors #464): `package.json`, `src-tauri/tauri.conf.json`, `src-tauri/Cargo.toml` + `Cargo.lock`, `deploy/download/index.html` VERSION, `CHANGELOG.md`, `tauri-build.yml` releaseBody (New in 1.4.3; 1.4.1 section rotated out).

Merging on green; after merge: tag `v1.4.3` → desktop/sidecar/vsix/hpc workflows → publish (with the release-body overwrite step — the asset-first workflow clobbers it, see v1.4.2 notes).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `391630a73ded`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
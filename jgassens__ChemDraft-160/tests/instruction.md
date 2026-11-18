# Issue

**Title:** Release 1.0.0

## Description

## Summary
- Version 0.3.9 → 1.0.0 in tauri.conf.json, apps/desktop/package.json, Cargo.toml and Cargo.lock.
- Website: the β-test banner and notices are removed (1.0 is the official release); the in-app bug-report line stays.

Both platform builds come from this PR's merge commit on main. The release notes (`ChemDraft_1.0.0_aarch64.md`), appcast.xml and latest.json land in the feed PR after the release is published, as with 0.3.9.

## Tests
Version-only change plus static site edits: `cargo metadata --locked` confirms the lockfile, `git diff --check` clean; CI runs the full suite.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `94f61c929ad7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
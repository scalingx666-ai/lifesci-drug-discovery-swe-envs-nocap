# Issue

**Title:** Release 0.3.6

## Description

## Summary

- Version 0.3.6 in `tauri.conf.json`, `apps/desktop/package.json`, `Cargo.toml` and `Cargo.lock`.
- Release notes `ChemDraft_0.3.6_aarch64.md`.
- `appcast.xml`: signed Sparkle entry for 0.3.6, generated from the stapled DMG (length 68785319, matching the published asset byte for byte). Keeps the three newest versions.

The GitHub release [v0.3.6](https://github.com/jgassens/ChemDraft/releases/tag/v0.3.6) is already published and its download answers 200 with SHA-256 `42ad7b34fdd2c54f7148dc81edb1b833388dc483c41f2e533f573d62597d5aa6`. Merging this PR makes Sparkle offer the update.

## Test plan

- [x] App notarized (Accepted), stapled, `spctl` accepted (Notarized Developer ID); `codesign --verify --deep --strict`
- [x] DMG notarized (Accepted), stapled, `spctl -t open` accepted
- [x] Bundled OPSIN JRE present in the app
- [x] Published asset downloads (200) and hashes identical to the stapled DMG

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d7f536c0cb3c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** fix(release): regenerate updater signing key (v1.4.1 build failed)

## Description

v1.4.1 build failed at updater signing on all platforms: `incorrect updater private key password: Wrong password for that key`. The original key was encrypted but the password secret was empty. Regenerated the keypair (verified it signs), swapped the public key in `tauri.conf.json`. Safe to rotate — no updater-enabled release shipped yet.

Needs secrets updated: `TAURI_SIGNING_PRIVATE_KEY` + `TAURI_SIGNING_PRIVATE_KEY_PASSWORD`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5222eeceb2c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Windows release workflow with SignPath Authenticode signing

## Description

## Summary
Addresses #166 (SmartScreen warns because the installer isn't code-signed).

- `.github/workflows/windows-release.yml`: `workflow_dispatch` only (inputs: `ref`, optional draft `upload_to_release`, optional `notes_file`); read-only by default, `contents: write` only on the upload job; never runs for pull requests.
- Build on windows-latest (Node, pnpm, pinned Rust, Temurin JDK for the OPSIN runtime), stable NSIS with updater signing opted out → SignPath Authenticode signing → minisign `.sig` computed over the **signed** installer → `latest.json`. Each signing step is skipped with a `::warning::` while its secret is unset, so the workflow can be dry-run now.
- `scripts/desktop-tauri.mjs`: `CHEMDRAFT_SKIP_UPDATER_SIGNING=1` opt-out (default unchanged); `tools/release/verify-windows-updater.ts` checks the `.sig` against the repo public key.
- `docs/releasing/windows-signing.md`: what the owner must do (apply to SignPath Foundation, project + GitHub trusted build system + signing policy, repo secrets/vars, `TAURI_SIGNING_PRIVATE_KEY`); `windows-updates.md` points at it. The VM release path stays valid.

## Tests
New tests for the opt-out and the verifier; full vitest 7293 passed; lint clean. Windows execution is unverified until the first workflow run.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d980c163f004`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
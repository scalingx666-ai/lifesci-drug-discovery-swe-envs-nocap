# Issue

**Title:** fix: single-ring native SMILES keeps the ring-closure bond order

## Description

The single-cycle SMILES fast path wrote a bare `1` for the ring-closure bond, dropping its order, so drawn Kekulé benzene exported as cyclohexa-1,3-diene (`C1C=CC=CC1`). The closure order now rides on the opening ring digit, matching the general writer.

Salvaged from an uncommitted change found in a stale Claude worktree during cleanup; re-applied on top of main with its test moved into the `describe` that defines the reparse helper.

- `pnpm lint` clean; `pnpm vitest run`: full suite green.
- Build stamp bumped.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fbdab8b47f64`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
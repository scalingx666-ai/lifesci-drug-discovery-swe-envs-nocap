# Issue

**Title:** fix(build): sync pnpm-lock specifier to ~2.9.0 (frozen-lockfile)

## Description

: lockfile still had `^2.9.0` while package.json is `~2.9.0`, breaking `pnpm install --frozen-lockfile` in CI (ERR_PNPM_OUTDATED_LOCKFILE). One-line lockfile resync.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f582f1f6c537`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Give the pwsh release-gate tests a 30 s timeout

## Description

## Summary

`tools/release/windows-release.test.ts` runs the Windows release workflow's signing-gate scripts in PowerShell. A cold `pwsh` start on CI runners can take longer than Vitest's 5 s default test timeout, and these tests have failed unrelated PRs today. Both `it.each` groups that spawn `pwsh` now take an explicit 30 s timeout (one shared constant with a one-line reason). What the tests check is unchanged.

The module-level `hasPowerShell` probe runs at import time, outside any test, so it was never subject to the 5 s limit.

## Tests

- `pnpm exec vitest run tools/release/windows-release.test.ts` on macOS with pwsh installed: 13/13 passed.
- CI's four checks run the full suite.

## Review

Opus (agentctl run-20261028-135409-515159): timeout in the right argument position for Vitest 3.2.4, applied to both pwsh-spawning groups, assertions unchanged. No findings.

## Platforms

Test-only change under `tools/`; no app, native or path code. Exercised on macOS; Linux and Windows run it in CI.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b55d564077c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
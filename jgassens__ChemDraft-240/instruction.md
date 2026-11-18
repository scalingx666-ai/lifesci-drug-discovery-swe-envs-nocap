# Issue

**Title:** Give tests 20 s on CI runners

## Description

## Summary

Shared CI runners, Windows especially, are slow on cold file scans and process spawns. Tests that sit near Vitest's 5 s default have been timing out intermittently and failing unrelated PRs today (the worker-chunk import audit on Windows, the fail-open timing test, and the pwsh signing gates that #237 fixed one by one). The root `vitest.config.ts` now sets `testTimeout` to 20 s when `CI` is set and keeps 5 s for local runs, so real hangs are still caught. #237's explicit 30 s pwsh timeouts stay and still take precedence.

## Tests

Config-only change. The config loads with and without `CI=1` (`tools/release/windows-release.test.ts` run both ways). CI's four checks run the full suite under the new setting.

## Review

Opus (agentctl run-20261028-141523-94143f): correct option and placement for Vitest 3.2.4; applies to every test the root config runs; per-test timeouts still win; local default unchanged; GitHub Actions sets `CI`. Approve.

## Not covered

- `hookTimeout` stays at Vitest's 10 s default, so a slow `beforeAll` on a cold runner can still time out.
- Any non-empty `CI` value (even `false`) selects 20 s.

## Platforms

Test configuration only; no app, native or path code.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f55ab1ace2b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
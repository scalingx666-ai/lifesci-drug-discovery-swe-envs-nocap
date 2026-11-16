# Issue

**Title:** Authenticate Codecov uploads with GitHub OIDC

## Description

## Summary
- Switch the Ubuntu 3.12 Codecov step to `use_oidc: true` with job-level `id-token: write`.
- Drop dependence on `CODECOV_TOKEN` / Codecov org admin UI (GitHub App is already installed on `ecrl`).

## Test plan
- [ ] CI `test (3.12)` Codecov step logs a successful OIDC upload (or a clear error we can act on)
- [x] Other CI jobs remain green
- [x] After merge to `master`, confirm https://app.codecov.io/gh/ecrl/padelpy starts receiving coverage (badge may lag)

Made with [Cursor](https://cursor.com)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7dff88fda02`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
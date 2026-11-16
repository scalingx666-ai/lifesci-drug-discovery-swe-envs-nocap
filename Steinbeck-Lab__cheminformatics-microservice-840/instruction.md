# Issue

**Title:** fix(frontend): bump vitest to 4.1.12 for npm audit

## Description

The Security audit step in the frontend test job fails on PR #839: @vitest/mocker <=4.1.11 has two moderate advisories (GHSA-qxg6-89mg-rqv8, GHSA-xp26-3454-mjgp). This bumps vitest and @vitest/coverage-v8 to ^4.1.12. npm audit now reports 0 vulnerabilities; all frontend tests pass.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f033e3bdbfd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
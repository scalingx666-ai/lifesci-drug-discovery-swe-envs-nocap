# Issue

**Title:** release: tooling cleanup from develop

## Description

brings #47 into main: dependabot removed, ruff include allowlist fix, typing modernization, python floor aligned to 3.9, mypy added to CI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b11d841e6043`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
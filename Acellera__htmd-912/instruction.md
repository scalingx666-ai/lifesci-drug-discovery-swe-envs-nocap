# Issue

**Title:** Fix ACEMD tests for untrusted PRs

## Description

- [x] Run ACEMD tests conditionally

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38795e8da60b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
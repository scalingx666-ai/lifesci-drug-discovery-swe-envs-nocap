# Issue

**Title:** Small fixes related to exceptions at the C APi boundary

## Description

Related to #303. The first examples now properly fails with `SMI Reader: unknown symbol: '{'`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84e883d4de71`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
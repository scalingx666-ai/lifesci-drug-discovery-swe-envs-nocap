# Issue

**Title:** Fix macOS workflows

## Description

Pins GCC 14 to avoid reported compilation errors with GCC 15. See

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `502d7c59bf88`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Prevent inclusion of .git directories in external/<XXX>.tar.gz

## Description

Such directories can get very large, and in turn increase greatly the size of the chemfiles repository.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `876fc14fb9e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
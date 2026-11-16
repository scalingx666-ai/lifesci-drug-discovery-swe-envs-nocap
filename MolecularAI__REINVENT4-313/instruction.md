# Issue

**Title:** correct scoring.toml

## Description

The parallel parameter is now an integer, not a boolean.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31b90474cabb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
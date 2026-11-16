# Issue

**Title:** Better check for exceptional floating point values

## Description

- also trap positive infinity when determining CN weights

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `438dbee3765f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
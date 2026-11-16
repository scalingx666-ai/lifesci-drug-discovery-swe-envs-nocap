# Issue

**Title:** Setup ci workflow

## Description

- setup CI workflow pipeline
- upon push on certain branches, will kick start the test job run on `unit` and `integrative` directories
- only files with .py, .sh, .yml apply

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c585341691a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** CI Updates

## Description

# Todo's

- [x] Add pyright to ci
- [x] Fix pyright issues (Not needed all are false flags of possibly unbound variables)
- [x] Switch to UV

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96ceeb33ef90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
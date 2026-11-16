# Issue

**Title:** Fix molecule and atom renaming

## Description

- [x] Enforce unique atom names
- [x] Clean up element guessing
- [x] Move atom renaming to `fftype` internals
  - [x] Update documentation
- [x] Update tests
- [x] Fix #524 
- [x] Fix #557
- [x] Fix #643 

This is a remake of #781 

Depend on

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `76cc1c1ba673`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
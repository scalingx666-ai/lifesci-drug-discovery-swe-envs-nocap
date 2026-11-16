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

~~Depend on #778~~

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `330655f6d03a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
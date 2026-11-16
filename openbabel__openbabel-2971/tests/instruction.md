# Issue

**Title:** fix bindings_php build issues

## Description

add forgotten CPP macro, correct filename, and take care of compatibility between GNU and BSD sed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7400a102d4ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
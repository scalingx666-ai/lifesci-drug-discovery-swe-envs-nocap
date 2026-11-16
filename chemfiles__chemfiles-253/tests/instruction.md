# Issue

**Title:** Initial SMI support

## Description

Warning: this code is a bit rough and fairly difficult to read. It will need to be refactored and all I can really guarantee is that is won't crash - probably.

Write support is terrible as it cannot current write rings, this will need to be fixed before it is merged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc375d2d5fdc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
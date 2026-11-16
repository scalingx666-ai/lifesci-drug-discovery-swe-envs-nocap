# Issue

**Title:** Update CI

## Description

## Description

Update CI:

* Remove Python `3.7` and `3.8` to reduce the size of the CI matrix
* Add `macOS-14` (M1) to CI matrix, only for Python `3.12`

## Checklist

- [x] Tests
- [x] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c65aa6df8389`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
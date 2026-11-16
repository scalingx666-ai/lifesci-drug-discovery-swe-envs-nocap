# Issue

**Title:** Fix CI

## Description

- fixes an issue that came up after latest mypy release
- reverses the sorting order in our FPS utility to make the results consistent with the new `fpsample>=1.0.0` release

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f4d1de2b8b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
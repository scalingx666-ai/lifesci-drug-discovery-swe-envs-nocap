# Issue

**Title:** Add GH actions OSX build

## Description

Migrate OSX testing from Travis CI to GHA.

Note:
- meson 0.56 fails on OSX again, pin to 0.55.3 for now

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8f3dc411ea62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
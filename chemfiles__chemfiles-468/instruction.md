# Issue

**Title:** Make MinGW builder faster on CI

## Description

This tries to make CI a bit faster (MinGW builder takes 25 min just to compile the code, vs 6-8 min on most other builders)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2140f89d126c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
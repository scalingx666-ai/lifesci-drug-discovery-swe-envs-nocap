# Issue

**Title:** Stop training early on NaNs

## Description

Should probably also skip eval when NaNs are encountered.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2598f591ed35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
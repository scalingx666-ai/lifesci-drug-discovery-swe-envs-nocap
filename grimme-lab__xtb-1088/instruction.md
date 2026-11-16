# Issue

**Title:** Remove `gcc-11` from CI on macOS as it got removed from the images

## Description

- remove `gcc-11`

Based on the following announcement:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f7eb69008003`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
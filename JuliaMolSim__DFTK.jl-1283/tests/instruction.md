# Issue

**Title:** Add julia version guards for GPU precompilation

## Description

Guard against broken GPU precompilation (#1278).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `480436ff66ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
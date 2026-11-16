# Issue

**Title:** fix(file): update position of cursor when writing

## Description

Currently one is able to write multiple frames to CSSR files. Chemfiles is able to read back only one and I guess the standard allows only one frame anyway. This is because the checks rely on the cursor position which is currently not updated when writing. So one can write multiple frames without triggering those checks.
Technically this also applies for appending, but this would require an implementation of `tell` for all different files. Since CSSR does not support appending (and it would not be sensible to support appending for any other one-frame format) we can safely ignore appending for now.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d2a1aefbe98`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
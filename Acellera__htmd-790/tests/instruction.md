# Issue

**Title:** Fix Molecule align

## Description

I don't know how this bug went unnoticed but aligning on a specific frame zeroed all other frames. Anyway, I also added now an option to align all frames to all of the reference

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d5f1f1e1322`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
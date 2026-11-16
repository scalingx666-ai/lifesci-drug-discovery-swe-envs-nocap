# Issue

**Title:** Fix writing of unit cells with negative values in extended XYZ

## Description

Fix #449 

I failed to consider that the entries in unit cell matrix can be negative.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b2bb532e4d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
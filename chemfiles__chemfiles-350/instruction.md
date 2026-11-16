# Issue

**Title:** More conservative fix for bonds detection

## Description

fix #301

Instead of changing the criterion for all atoms as in #315, the same criterion is kept but the radii of C/O/H/N/S/F are changed.

This should make the code working while we look for a better bond perception algorithm

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7a3848962c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
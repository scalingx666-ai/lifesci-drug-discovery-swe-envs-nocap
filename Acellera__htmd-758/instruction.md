# Issue

**Title:** Bugfix for PDBs with missing occupancy or beta values

## Description

Fixed an issue when reading files where not all atoms have occupancies or beta values set by defaulting empty fields to 0 if they are to be stored in a floating point array.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `abf234355489`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
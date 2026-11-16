# Issue

**Title:** Fix/cell matrix

## Description

While using the matrix of the `UnitCell` for some computations I noticed that in some cases one gets a unit matrix but the cell parameters (`a`, `b`, `c` and angles) are correct. There were some missing `update_matrix` calls.
This happens when reading e.g. a .gro file with 9 cell entries.

Also added some test for that :)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b06c7583ba7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** fast restore symmetry

## Description

Fast version of the restore symmetry subroutine:
- 2D -> 1D 
- copy the sign of the elements
- sort (by absolute value)
- average nearby elements
- back transformation 1D -> 2D
- minimal amount of OMP
- the main loop can be parrallelized (TODO)
- A test to compare the result with the original restore_symmetry is commented in restore_symmetry

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cbf6eeb2eda6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
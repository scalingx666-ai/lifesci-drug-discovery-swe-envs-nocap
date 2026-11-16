# Issue

**Title:** Allocate set%ffnb dynamically.

## Description

The array used for the adjustment of the GFN-FF neighbor list (set%ffnb) is now allocated dynamically.
The first dimension is always the maximum number of neighbors allowed in GFN-FF (42 since 6.7.1) and the second dimension is the number of atoms that the neighbor list should be adjusted for.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1779d8afafb7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
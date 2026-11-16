# Issue

**Title:** Overlap gradient rework

## Description

- explicit E-coeffiecient gradients up to f-orbitals
- resort orbitals and fix cartesian-spherical transformation
- remove tests and support for f-orbitals
- calculate overlap gradient as triangular matrix

The support for f-orbitals was removed due to a possibly wrong ordering in the tblite transformation matrices. Hence, we do not have a reference at the moment.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `28f1ef987d5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
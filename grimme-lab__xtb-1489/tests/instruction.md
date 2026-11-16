# Issue

**Title:** fix DOF optimization for fixed atoms

## Description

This change reworks the projection done in the optimizer and uses the infrastructure of the projection of rotations and translations introduced in #1435 .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9040512dd7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
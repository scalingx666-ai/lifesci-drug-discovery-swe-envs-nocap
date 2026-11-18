# Issue

**Title:** Initial commit

## Description

ESP works in the MPI code. SCF is MPI parallelized, ESP part is not yet.
Additionally, cleaned up the oeproperties module by removing allmods and implicit
variable definitions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d6cf2d4e0b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
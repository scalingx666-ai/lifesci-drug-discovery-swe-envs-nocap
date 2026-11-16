# Issue

**Title:** fix adaptive base for saving PDBs

## Description

Simplify the writing of new coordinates that works also when the new coordinate file is a PDB.

The previous optimization is probably not important as this is not a critical part for performance

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3093c0fa592a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
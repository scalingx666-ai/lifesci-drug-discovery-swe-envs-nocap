# Issue

**Title:** Linear atoms in metallocycles

## Description

Add an issue template
Fixes bug in SMILES builder where linear atoms within rings raised a ValueError
Adds fallback to previous minimisation build if builder fails

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eab9fdc83727`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
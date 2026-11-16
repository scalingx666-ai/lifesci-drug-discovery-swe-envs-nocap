# Issue

**Title:** from_smiles descriptors are returned in the same order as input SMILES

## Description

This is an update for issue #20 that I created yesterday. It changes the default behaviour of `from_smiles` to return the molecular descriptors in the same order as the input SMILES strings.

Best,
Sebastian

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7998b9261224`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** mol2rdkit_phys_chem: make failure on any error optional

## Description

Add a parameter fails_on_any_error to MolToRDKitPhysChem to get partial results when the computation of a single physchem descriptor fails.

This feature is necessary for data analysis, where we want to examine data even if one of 200 descriptors failed to be calculated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37d8a76a3677`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
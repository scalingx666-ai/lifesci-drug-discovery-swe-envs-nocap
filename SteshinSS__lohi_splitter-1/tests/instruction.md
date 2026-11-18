# Issue

**Title:** Update the rdkit implementation for getting the fingerprints

## Description

AllChem.GetMorganFingerprint is deprecated in the most recent version of rdkit and returns a warning that is painful to the eyes, so updated the newer implementation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec43494fc6be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
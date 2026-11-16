# Issue

**Title:** Fingerprint generation

## Description

Changed the fps_from_smiles method. Now it does not store the mol object list in memory, which would be a problem for large data sets. If skip invalid, those fps are delete from the np array. 

Added a test to assert the deletion of the fps and the identification of the invalid smiles.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff9daa8fb801`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
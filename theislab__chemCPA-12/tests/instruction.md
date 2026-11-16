# Issue

**Title:** Fix featurizer

## Description

Added a check for '*' in smiles strings -> unknown atoms 
- close #1

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f5c79674c11`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
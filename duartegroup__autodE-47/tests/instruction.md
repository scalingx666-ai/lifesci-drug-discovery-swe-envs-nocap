# Issue

**Title:** Hotfix

## Description

- Aromatic hetereoatoms now have the correct default vacancy
- Search for bracketed metal atoms in a SMILES string to prevent Cn being considered as a metal, when it's a carbon followed by an aromatic nitrogen
- Added test for aromatic triazole

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c4dabef48013`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
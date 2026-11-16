# Issue

**Title:** Further updates for SMILES API changes

## Description

- Add `smiles` property to compound (alias for `absolute_smiles`)
- Add deprecation warnings for `isomeric_smiles` and `canonical_smiles`
- Add `smiles` and `connectivity_smiles` to the property map.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e7f8f814f74`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** API Change for SMILES types

## Description

Sometime in 2025, the PubChem API changed the way it handles SMILES strings.

From the glossary: https://pubchem.ncbi.nlm.nih.gov/docs/glossary#section=SMILES

The former "Canonical SMILES" property in our compound records has been replaced by a newly-named "Connectivity SMILES"

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2ba3fc78cff2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
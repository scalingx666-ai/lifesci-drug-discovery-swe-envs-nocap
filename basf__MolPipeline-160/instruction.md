# Issue

**Title:** rdkit_phys_chem: set empty descriptor list to default list

## Description

Empty descriptor list would lead to unusable MolToRDKitPhysChem. Now, if an empty list is given it's replaced by the default descriptor list.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b08074e660e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
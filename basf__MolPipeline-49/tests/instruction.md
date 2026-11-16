# Issue

**Title:** Block logs for physchem descriptors

## Description

This is only temporally, as long [fp_density](https://github.com/rdkit/rdkit/blame/db0e71bc1c002fa1f0fdc4f678488b6d1464d7aa/rdkit/Chem/Descriptors.py#L202) is using deprecated code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0144baf2c3a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** PySCF: Add support for recording dispersion energy

## Description

See https://github.com/pyscf/pyscf/blob/8b3fef8cf18f10d430261d4a8bea21fadf19bb1f/pyscf/scf/hf.py#L1054-L1076.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d5b72de4bb0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
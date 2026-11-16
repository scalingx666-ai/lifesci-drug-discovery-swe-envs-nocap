# Issue

**Title:** PySCF: Capture dispersion energy in scf_summary

## Description

Allows to correctly print PySCF the dispersion contribution from a `mf` object.

See See https://github.com/pyscf/pyscf/blob/8b3fef8cf18f10d430261d4a8bea21fadf19bb1f/pyscf/scf/hf.py#L1054-L1076.

 
Requires #194

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee8b54f1195e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
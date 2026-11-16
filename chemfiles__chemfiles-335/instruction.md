# Issue

**Title:** Fix a bug in PDB::forward

## Description

Without this chemfiles would only find 152 steps inside `data/pdb/ase.pdb` instead of the expected 156

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99486730d484`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
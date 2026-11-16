# Issue

**Title:** Numint reset

## Description

- new patched PySCF and GPU4PySCF grid classes for disabling grid sorting
- proper handling of initialize_grid for GPU4PySCF
- implement reset method in SkalaNumInt required by GPU4PySCF

Closes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `123a7ce09ef2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
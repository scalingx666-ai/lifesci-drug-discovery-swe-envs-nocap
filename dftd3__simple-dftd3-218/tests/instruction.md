# Issue

**Title:** Finish PySCF PBC interface + test reorg

## Description

- Completes the PySCF PBC integration (cell periodicity was included, but missing type hints + cell stress) 
- 
- Moves tests out of the package source so they're not importable

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a25531005ced`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
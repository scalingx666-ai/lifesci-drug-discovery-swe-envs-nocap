# Issue

**Title:** Refactor basis

## Description

- replace unused `Basis_Type` (copy from tblite) with `Basis`
- fixed dtype related RuntimeError in tests by explicitly setting dtype in reference data (to `torch.float64`)
- fixed settings

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `22e568074963`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix CEw and API keyword check after refactor

## Description

## Remarks on changes

- `found_keyword` should search for `BASIS` and not `BASIS=` because it expects either a space or `=` character after
- `run_quick` does not appear to need `delete_cew_vrecip` so it was removed
- `hrr_lri` needs indices `III` and `JJJ` from `quick_basis_module`. This was working correctly before when we imported everything from `quick_basis_module`, but after refactor, `III` and `JJJ` were mistakenly redeclared as local variables. These were removed and instead imported from `quick_basis_module` so `hrr_lri` sees them.

Sander tests in `qmmm_Quick/QMMM_MD_cEw` pass.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `57615234ac96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
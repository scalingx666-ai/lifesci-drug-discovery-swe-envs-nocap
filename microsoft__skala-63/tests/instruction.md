# Issue

**Title:** Fix grid alignment padding mismatch with gpu4pyscf

## Description

Set grids.alignment=1 in _build_grids_unsorted to prevent PySCF/gpu4pyscf from appending zero-weight padding points that cause size mismatches in Skala's feature generation pipeline.

- Force alignment=1 in _build_grids_unsorted with debug log when overriding
- Add ValueError check in generate_features when grid sizes don't match
- Add negative test confirming ValueError fires without the fix

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67449daf3660`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
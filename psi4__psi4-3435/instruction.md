# Issue

**Title:** Fix Tensor2d::back_transform dimension error in DF-MP2 gradients

## Description

## Description
Fix dimension mismatch in `Tensor2d::back_transform()` that caused DF-MP2 gradient calculations to fail. The temporary tensor was created with incorrect dimensions, leading to GEMM validation errors during OPDM/TPDM backtransformation to the AO basis.

Close #3433

## User API & Changelog headlines
- [x] Fixes DF-MP2 gradient calculations that previously crashed with `Tensor2d::gemm dimensions are NOT consistent!`

## Dev notes & details
- [x] Changed `back_transform()` temp tensor allocation from `(a->dim1_, transformer->dim2_)` to `(a->dim1_, transformer->dim1_)` to match matrix dimensions in the backtransformation: `G_AO = C * G_MO * C^T`
- [x] Fixes all DF-MP2/OMP2 gradient calculations
- [x] Added regression test: DF-MP2 gradient on charged open-shell quintet (Fe+)

## Checklist
- [X] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7747574febf5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
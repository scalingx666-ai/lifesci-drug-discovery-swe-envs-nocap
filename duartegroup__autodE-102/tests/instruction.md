# Issue

**Title:** Numerical hessians

## Description

Adds functionality to calculate numerical Hessians for any EST method with implemented gradients. 


- [x] `calc_hessian`
- [x] ~`calc_hybrid_hessian` (see ORCA manual)~ Will add in a different PR
- [x] numerical hessian impl with and without central differences
- [x] Update changelog
- [x] Add tests
- [x] Check that there aren't any `freq` or `hess` keywords in the keywords of the `calc_hessian` keywords argument
- [x] Parallelise
- [x] Fix QChem gradient extraction
- [x] Self review

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8bdab6a05b0b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** fix CI and stdsuite: add HF Hessian refs, density-fitted

## Description

<!-- Thank you for your contribution! -->

## Description
- [x] As it says on the tin. These aren't tested here (psi4 is the only harness set up for density-fitting), but I have used them in psi4 stdsuite machinery, so format, etc. good.
- [x] Fix CI that had deteriorated after 2 months and a psi release. Had to pin to older d4 temporarily.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c171e80c51af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
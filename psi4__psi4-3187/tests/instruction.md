# Issue

**Title:** Least Squares Tensor Hypercontraction (LS-THC) for ERIs (Part 2): Grid Pruning

## Description

## Description
This PR implements the grid pruning scheme of Matthews (https://pubs.acs.org/doi/10.1021/acs.jctc.9b01205), applying a pivoted Cholesky decomposition to the S matrix to remove linear dependencies and drastically reduce the number of grid points. Per @PhillCli's comments on #3157, taking the pseudoinverse of the S matrix can be costly, and this PR fixes that problem! The final rank appears to be _mostly_ invariant to grid size, but only to the molecule/basis set (results in tables below)

| System | Radial, Spherical Points | Initial Rank | Final Rank |
| ------------- | ------------- | ------------- | ------------- |
| Water/cc-pVDZ  | (25, 50) | 2605 | 280 |
| Water/cc-pVDZ  | (50, 86) | 8739 | 280 |
| Water/cc-pVTZ  | (25, 50) | 2630 | 1184 |
| Water/cc-pVTZ  | (50, 86) | 8774 | 1328 |
| Benzene/cc-pVDZ | (25, 50) | 9831 | 3124 |
| Benzene/cc-pVDZ | (50, 86) | 32588 | 3414 |

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Drastically reduction of the rank of the intermediates in a THC factorization

## Questions
- [x] The pivoted Cholesky algorithm presented by Matthews requires the upper triangular form. I modified the algorithm in matrix.cc to the upper triangular form because `Matrix::pivoted_cholesky` is not called elsewhere. Is this okay?

## Checklist
- [x] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7245e70546a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
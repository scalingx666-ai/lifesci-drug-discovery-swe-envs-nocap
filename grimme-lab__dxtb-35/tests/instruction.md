# Issue

**Title:** Calculation of Born radii

## Description

Calculation of Born radii according to [Onufriev-Bashford-Case model](https://doi.org/10.1002/prot.20033).

- [x] translate tblite version
- [x] vectorize
- [x] make batchable
- [x] autograd

Note: The reference values for the tests are taken from the `tblite` version. However, there was a  which requires recalculations. For now, I just took the values provided by `tblite` with the bug fixed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ba3a7adf9642`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
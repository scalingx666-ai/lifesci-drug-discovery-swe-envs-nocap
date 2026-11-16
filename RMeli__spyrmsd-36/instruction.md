# Issue

**Title:** Automatic fallback to explicit computation of maximum eigenvalue

## Description

## Description

Fix #35. 

The `lambda_max` function (which finds the highest eigenvalue of the matrix K as a zero of the characteristic polynomial) is subject to numerical errors for structures with a small number of atoms that superimpose perfectly. This PR adds an automatic fallback to the explicit computation of the eigenvalues of K, which appears to be more robust (inspection of the eigenvalues show they are almost degenerate, corresponding to very close roots of the characteristic polynomial). This is however slower and alternative, faster, solutions should be explored (see issue #35 for discussion).

Additionally, the tolerance for numerical errors in structures that can be superimposed perfectly is exposed in the API. 

## Checklist

- [x] Tests
- [x] Documentation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ab1f534c4a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
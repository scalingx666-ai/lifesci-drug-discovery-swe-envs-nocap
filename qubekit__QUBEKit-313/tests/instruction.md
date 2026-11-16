# Issue

**Title:** Vsite distance regularisation

## Description

## Description
This PR adds vsite-parent distance regularisation to the objective function using L1 regularisation.

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [X] add tests

## Questions
- [x] The performance of the vsite fits will be slightly different as the mean absolute error is now compared in the objective function rather than the sum of the absolute error and so very slightly different positions and charges will be selected. Do we need to benchmark this change in the default performance?

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea53fa6fbc68`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Faster and more robust dihedral fitting procedure

## Description

- [x] Use radians internally
- [x] Use a gradient-based local optimizer
  - [x] Implement analytic gradients
  - [x] Tests against numerical gradients
- [x] Fix multiple dihedral fitting
- [x] Report local optimization results
- [x] Clean up
- [x] Update tests

Depends on

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68bea8ca0984`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
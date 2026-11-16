# Issue

**Title:** Improved stochastic sampling

## Description

Sampling randomly from the dihedral space randomly is almost certainly less efficient than sampling more evenly, this PR adds an initial set of points well distributed

- [x] Implement point initialisation
- [x] Initialise `SGlobalDihedralOptimiser` at each point
- [x] ~Remove test .cpp and make file~ Convert to Catch2 tests
- [x] ~Update changelog~ included in #61

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a19e9dd35a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
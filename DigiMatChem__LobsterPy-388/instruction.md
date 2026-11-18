# Issue

**Title:** fix sitewise bwdf

## Description

# Todo

- [x] Enable icoxx normalization using number of electrons from `GROSSPOP.lobster`
- [x] Add sitewise bwdf stats method
- [x] Add atom pairwise bwdf stats method
- [x] Add asymmetry index stats method
- [x] Update plot-bwdf cli action to include missing options from BWDFplotter
- [x] Include references in docstring of featurizers
- [x] Add tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `123d346ec9a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
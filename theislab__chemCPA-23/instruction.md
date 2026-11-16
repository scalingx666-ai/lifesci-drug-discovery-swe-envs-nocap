# Issue

**Title:** Remove the one hot encoding

## Description

Adds indices to dataset + model, to remove the need for creating large OHEs when training on LINCS. For now the adversarial classification loss is just a Cross Entropy loss over all drugs, this should be fixed with #22

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a08f65aaa2c5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
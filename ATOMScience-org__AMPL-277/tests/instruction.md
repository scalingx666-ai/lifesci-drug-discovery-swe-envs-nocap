# Issue

**Title:** Optimize MTSS split for similarity of response value distributions across split subsets

## Description

Added a new MTSS parameter and a fitness function term to allow optimizing a scaffold split so that the response value distributions in the training, validation and test sets are as similar as possible. This addresses a common problem with scaffold splits, especially of small datasets, where the validation and/or test set performance metrics look bad because a model wasn't trained on the full range of values found in the test sets.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed92c46647a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
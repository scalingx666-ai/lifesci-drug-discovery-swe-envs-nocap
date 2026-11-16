# Issue

**Title:** Make disentanglement model non-linear

## Description

The non-linear disentanglement loss is replaced by a MLP with 2 hidden layers.
During the hparam sweeps most adversarial classifiers had dimensions 64 with 2-3 hidden layers, so now the model we use during eval is similar.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9866bbbb4be7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
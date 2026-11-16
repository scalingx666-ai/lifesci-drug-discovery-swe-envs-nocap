# Issue

**Title:** add sample weight and balancing to Chemprop

## Description

- Adds kwarg `sample_weight` to all ChemProp models
- Adds kwarg `class_weight` to `ChempropClassifier`.
- Add unit test for forwarding the weights.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c2228e0df84`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
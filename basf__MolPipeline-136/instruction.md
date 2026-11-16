# Issue

**Title:** Fix: kwargs fails for Neural Fingerprint

## Description

This PR fixes the failing initialization of the NeuralFP with kwags, described in this [issue](https://github.com/basf/MolPipeline/issues)

**Problem:**
The error is caused by setting `disable_fitting` after calling `super().__init__`, which requires  `disable_fitting` to be defined. Move setting of parameter before initialization

**ToDos:**
- [x] Write unit-test to reproduce error.
- [x] Fix Error

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2ff8eb3b1a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
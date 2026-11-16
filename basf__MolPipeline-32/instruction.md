# Issue

**Title:** 31 add kwargs to chempropneuralfp  init

## Description

- Minor changes in `neural_fingerprint.py`  
  - Created separate tests for `ChempropNeuralFP`
  - Reworked `test_models.py` to avoid duplicate code
  - Created `chemprop_test_utils`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `60370d50bb93`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
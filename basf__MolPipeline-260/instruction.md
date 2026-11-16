# Issue

**Title:** Restructure splitters

## Description

ToDos:
- [x] Move GroupShuffleSplit and create_continuous_stratified_folds to separate files
- [x] transfer create_continuous_stratified_folds  to StratifiedRegressionKFold

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c826aa21d7e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
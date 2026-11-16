# Issue

**Title:** MurckoScaffold Fix

## Description

*Issue #, if available:*

Addresses #84 

*Description of changes:*

Replaced `MurckoScaffoldSmiles` with `AllChem.MurckoDecompose` and deleted `includeChirality` arg in `ScaffoldSplitter.train_val_test_split`, `k_fold_split` and `test_splitters.py` 

By submitting this pull request, I confirm that you can use, modify, copy, and redistribute this contribution, under the terms of your choice.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75acff50ba74`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
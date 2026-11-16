# Issue

**Title:** cleanup up context parallel class names and test locations

## Description

Will make this easier to re-use for Llama3
* renames (and moves) `ContextParallelDataLoaderWrapper` to collator.py
* renames CP data collator to `DataCollatorForContextParallel`
* moves tests for `ContextParallelDataLoaderWrapper` to the esm2 model recipe

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e0b862430c99`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
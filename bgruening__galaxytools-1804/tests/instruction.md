# Issue

**Title:** Fix split=None in the train_test_split tool

## Description

Fixes the issue: 

Also, adds a test for `shuffle=None`

ping @gdefazio @bgruening thanks!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9c5423ba96f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
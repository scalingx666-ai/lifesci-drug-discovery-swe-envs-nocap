# Issue

**Title:** fix python 3.13+ compat

## Description

our method for monkey patching the forward method of predictors for uncertainty estimation was actually based on a Python 3.11-12 bug which has now been patched in 3.13+, so this changes the approach to do something different that should be compatible across all versions

see this issue for more details about the bug fix: 

@KnathanM please review RE: our offline discussion. have not tested this yet, going to let the CI handle it

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9dfa701a0a67`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
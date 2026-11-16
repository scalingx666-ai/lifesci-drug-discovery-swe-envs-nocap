# Issue

**Title:** Small changes to LINCS config

## Description

@MxMstrmn Just for you to have a quick look.

I increase the epochs by a lot, I think it's fine to only terminate the training if we either run out of time, or do early stopping.

In the test runs there were some problems with the disentanglement loss being very high, hence I remove the `adversary_steps=5` option.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `02b7fd64d382`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
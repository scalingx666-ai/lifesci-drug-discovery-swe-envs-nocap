# Issue

**Title:** Enable wandb to be used for metric logging in pytorch implementation

## Description

This PR enables for wandb to be used with the pytorch implementation. It also allows for wandb to be configured via a "wandb" section in the config file.

This implementation only logs metrics to wandb.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `11ec725df81e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
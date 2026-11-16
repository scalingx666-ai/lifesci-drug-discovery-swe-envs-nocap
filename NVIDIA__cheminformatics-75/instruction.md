# Issue

**Title:** Change to run multiple benchmark tests parallel...

## Description

Change to run multiple benchmark tests parallel. This script will create isolated instance of the applications for parallel runs. With this following are variable:
 - Checkpoint to be used for inferenceing
 - GPU selection
 - Execution ID for result folder

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f4532810b93`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
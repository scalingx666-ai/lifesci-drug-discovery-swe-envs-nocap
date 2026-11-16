# Issue

**Title:** misc + selu

## Description

This PR includes miscellaneous changes to the code base. Of note:

- [x] Replace ReLUs with SELU for improved performance
- [x] Add Xavier initialization
- [x] Add reference model which has ~98% on validation set

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `122cdc3470d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
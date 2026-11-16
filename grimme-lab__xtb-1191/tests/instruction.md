# Issue

**Title:** Update OpenMP parallelization in WSC to avoid data-races

## Description

This PR removed data-races from shared minpos/mindist/nminloc/nmindist. Now, `wsc` and `peeq` tests should be repeatable.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ae3b5568795`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
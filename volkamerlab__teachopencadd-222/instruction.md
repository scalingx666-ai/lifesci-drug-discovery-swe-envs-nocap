# Issue

**Title:** Fix CI failures

## Description

## Description
This PR aims to fix CI failures involving RDKit installation on MacOS and T018 with failing API request of DogSiteScorer.

## Todos
- [x] fix RDKit installation on MacOS (pin fontconfig)
- [x] fix T018 with failing API requests of DogSiteScorer
- [x] fix tensorflow AttributeError only seen for MacOS  (pin h5py)
- [x] seeing dead nb kernel for MacOS

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7dd2a8113761`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
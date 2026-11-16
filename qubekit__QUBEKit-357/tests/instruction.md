# Issue

**Title:** Fbopt workqueue

## Description

## Description
ForceBalance uses only one core by default. Here we employ the workers from the ndcctools package to help parallelise the process. 

## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da7a60bc2750`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Allow ANI to be used to calculate the hessian

## Description

## Description
This PR fixes a bug where we assumed the wbo matrix was also calculated with the hessian. This means the wbo matrix will be missing later which will cause issues when using hessian fitting with QForce. 


## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `258ee117f3b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
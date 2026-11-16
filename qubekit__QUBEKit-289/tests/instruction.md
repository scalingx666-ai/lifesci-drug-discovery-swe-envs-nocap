# Issue

**Title:** Torsiondrive seed conformers

## Description

## Description
This PR adds the option to pass seed conformers to torsiondrives, which would allow pre-optimised conformers to be used in future. The seed conformers are also written locally. 

This PR also reworks how many workers are set up during torsiondrives to split the resources more efficiently. Now the number of workers at each iteration of a torsiondrive will be `min([n_jobs, n_workers])` where `n_jobs` is the number of grid points to optimise and `n_workers` is the maximum number of allowed workers.  

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [x] add tests

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90f83f21c8ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
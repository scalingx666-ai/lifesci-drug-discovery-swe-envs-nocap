# Issue

**Title:** Base branch for CI/env fixes

## Description

## Description
Current `teachopencadd` has a couple of dependency conflicts and deps-unrelated `pytest` fails.
This base branch shall be used to get a fully passing CI, while fixing all the different bits and pieces in smaller PRs.

## Todos
- [x]  -- pin `numpy<1.24` and unpin `tensorflow`; do not test T021/22 and deal with it later (see below)
  - [x] #299 
- [x] 
  - [x] #152 
- [x] 
  - [x] #300 
- [x] 
  - #303 --- do not close before at least Feb
- [x] 
  - [x] #298
- [x] 
- [x] 
  - [x] 
  - [x] 
- [x] #310
  - Fixed in 
- [x] Unpin `fontconfig` because  seems fixed?
  - Seems fine, all tests are passing as before after 

## Notes: After this PR's merge
...continue with TODOs in #312

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c4b57ebdf46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Parameterize: limit concurrent jobs

## Description

- [x] `PlayQueue`:
   - [x] Limit concurent jobs
   - [x] Implement `PlayQueue.max_jobs`
- [x] `parameterize`: implement `--max-jobs` argument

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0ff95931934`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
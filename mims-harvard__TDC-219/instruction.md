# Issue

**Title:** rdkit change caused failed circle-ci build

## Description

Fixed
https://app.circleci.com/pipelines/github/mims-harvard/TDC/614/workflows/9dd4eb51-98e1-4c41-8b5a-6fbd552584ba/jobs/619

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b22573878957`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
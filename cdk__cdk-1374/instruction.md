# Issue

**Title:** cdk-datadebug isolate

## Description

Removes internal uses of cdk-datadebug. There was a single IO test, I think it is okay to drop this test and remove the dependency of modules on cdk-datadebug. It is useful but not integral.

Oh an another null check fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5010c2434d1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
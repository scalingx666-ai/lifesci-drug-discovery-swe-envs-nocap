# Issue

**Title:** Add 404 checks to our docs deployment pipeline

## Description

In case one of the links break or we are maybe linking to non-public resources.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a56cc5dc07e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
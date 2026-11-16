# Issue

**Title:** Make pyright a seperate test job

## Description

As discussed in issue  we have currently problems with pyright that leads to fails in the linting pipeline, so we currently ignore the linting pipeline when looking at PRs, which is not good, because one does not see on the first glance if there are maybe also problems with ruff etc. 

This PR makes pyright a seperate pipeline job so that one sees if there are other issues.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f79004d3d2a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
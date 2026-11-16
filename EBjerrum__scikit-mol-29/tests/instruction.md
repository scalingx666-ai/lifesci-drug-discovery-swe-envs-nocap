# Issue

**Title:** Skopt

## Description

Casting arguments before calls to rdkit functions, to enable integration with tools that sets parameters with 'exotic' numpy dtypes (e.g. skopt)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a95a3d60876b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
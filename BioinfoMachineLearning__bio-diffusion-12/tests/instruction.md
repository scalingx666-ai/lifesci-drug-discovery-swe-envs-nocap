# Issue

**Title:** Move environment variables above sys deps in Dockerfile

## Description

Move environment variables in Dockerfile (to avoid and yes/no interactive prompts in the system dependency install steps)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4034d24ea649`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Bump image for doc pipelines

## Description

In the doc pipelines, we are still using Ubuntu 20.04, which is not anymore supported by github, here we change to `ubuntu-latest`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5025ad7eff57`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
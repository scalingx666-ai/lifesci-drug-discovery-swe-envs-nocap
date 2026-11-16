# Issue

**Title:** Add workflow for deploying GitHub pages

## Description

With this we can deploy GitHub pages directly from the actions pipeline, no need to have a separate branch with the source of the pages.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b01a25f7926`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
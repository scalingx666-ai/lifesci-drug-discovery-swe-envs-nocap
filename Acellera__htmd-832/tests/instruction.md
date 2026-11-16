# Issue

**Title:** Fixes conda-build

## Description

`conda build` of htmd was no longer working anymore with the latest version of `conda-build`. This fixes it. It's urgent and necessary to be merged on other branches as well.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2af298842483`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
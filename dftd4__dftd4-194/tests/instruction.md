# Issue

**Title:** Provision CI from conda-forge

## Description

Using conda environments to provision the dependencies for CI testing seems more stable than using the base images.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `488e35b59e13`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
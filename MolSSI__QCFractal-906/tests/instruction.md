# Issue

**Title:** Use 0 initial blocks in parsl

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Currently, we have parsl use 1 initial block. This means a slurm job (or similar) will be created even if the manager doesn't get any jobs at startup.

This PR sets that to zero, so no slurm jobs should be created in that scenario.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05e4223dac65`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** [Dataset] Fix for Downloading Datasets

## Description

As reported by @cyhFlight, the package should download datasets only when they are not found.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc96092816f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
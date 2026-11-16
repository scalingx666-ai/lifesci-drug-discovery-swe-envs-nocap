# Issue

**Title:** fix PKNCAconc & PKNCAdose: exclude before timecheck

## Description

Updated the concentration-time validation in `PKNCAconc.data.frame` so that excluded points (as indicated by the `exclude` column) are not considered during checks. Added a test to verify itt in `test-PKNCAconc` errors are not produced.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `23ce7b787655`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
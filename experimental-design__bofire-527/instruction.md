# Issue

**Title:** nonlinear constraints without torch

## Description

This PR should remove errors thrown when using nonlinear constraints without torch being installed.  .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `748fd9ee6da8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
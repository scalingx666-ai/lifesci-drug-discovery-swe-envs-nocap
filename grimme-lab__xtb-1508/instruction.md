# Issue

**Title:** Pass mass instead of number density to reference state

## Description

This removes a further implementation discrepancy with tblite.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24211bd6cb87`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
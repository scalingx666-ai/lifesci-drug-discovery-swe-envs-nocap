# Issue

**Title:** Support docking with tblite Hamiltonians

## Description

Adds support for docking based on tblite Hamiltonians. Tests against the native implementation are consistent within the fluctuations of the aiss algorithm

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3af6086e2931`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Support ONIOM with tblite Hamiltonians

## Description

Adds tblite backend support to ONIOM. Checks that the initial charges are both EEQ-based (however, they differ quite a bit). The final energy differences are much smaller. Tests against the values from the native implementation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8487759b3b8f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
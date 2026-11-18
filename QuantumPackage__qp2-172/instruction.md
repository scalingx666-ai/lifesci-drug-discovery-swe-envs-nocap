# Issue

**Title:** Fix for `Floating-point exception` during the calculation of Ncsf

## Description

Fixed the bug due to 0 in LogGamma[Ms].

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4ddbe3933850`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
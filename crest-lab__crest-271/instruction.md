# Issue

**Title:** Fix for making ALPB h2o compatible with tblite calculator

## Description

tblite calculations only recognized the 'water' keyword, but not 'h2o'.
Implemented a fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9967345ee201`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
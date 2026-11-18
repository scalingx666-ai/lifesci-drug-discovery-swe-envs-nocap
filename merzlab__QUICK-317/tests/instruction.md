# Issue

**Title:** G function trap

## Description

1) Add trap to quit with error message if a user tries to use G functions.
2) Remove SAD guess that was made for basis sets / elements with G functions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea3a84d2c09c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** fix automatic plotting for large structures

## Description

by skipping to display all plots but instead saving them to a file when more than 20 inequivalent ions are found in the structure.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9be3ff494ea5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
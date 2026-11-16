# Issue

**Title:** overflow when raising nprocs to power

## Description

This should fix some overflow issues with even selection. Running the test suite now.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c18969e38c1a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Attempts a testing environment for the cookiecutter

## Description

This should provide a way to test the cookie cutter. It is not exactly bulletproof, but will check and make sure that the conda or pip environments are setup correctly. .

If you could add this repo to travis, I would be curious to see how far this gets.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b10f563d7a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
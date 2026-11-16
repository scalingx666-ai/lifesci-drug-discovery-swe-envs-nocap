# Issue

**Title:** Not treating Inchi warnings as errors.

## Description

Treating warnings as errors led to some valid molecules causing
errors because their stereochemistry could not be assigned.
 on GitHub.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e5c267aa9711`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
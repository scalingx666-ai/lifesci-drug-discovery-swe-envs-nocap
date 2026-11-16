# Issue

**Title:** BUGFIX: styles not applied to phonon-bandplot from CLI

## Description

User style arguments were not being passed correctly to the phonon dos plotter.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55b4a9010146`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
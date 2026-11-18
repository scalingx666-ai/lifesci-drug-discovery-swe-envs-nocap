# Issue

**Title:** Fix NCI RDG cube misclassified as high_field

## Description

- **Add per-frame bond detection for trajectory GIFs**
- **Fix RDG cube misclassified as high_field due to outliers**

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b83cadc20e2c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Bugfix for QCG

## Description

- Fixes a Bug in the crest version 2.12 that lead to a crash of the ensemble generation during the QCG run
- Fixes a Bug regarding the QCG when compiling with gfortran. This also affects builds with conda

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `697a7a560173`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Deep learning edition fixes for colab compatibility

## Description

Various fixes to make the DL edition notebooks run more smoothly on Google colab.

- T033: allow custom widgets
- T035: remove unnecessary numpy constraint
- T037, T038: remove unnecessary pandas constraint

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58e6e28475c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
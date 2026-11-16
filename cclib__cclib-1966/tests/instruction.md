# Issue

**Title:** Psi3: remove parser

## Description

Psi3 hasn't been released or maintained meaningfully since 2011 and our parser never received proper unit test data.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d399d3c60c0c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
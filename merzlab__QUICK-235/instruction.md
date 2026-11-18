# Issue

**Title:** Rolling back to old analytical sswder implementation in host code

## Description

In a previous PR I disabled numerical sswder in device code; but I forgot to do the same in host code. In this PR, I have done this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `30412bba8703`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
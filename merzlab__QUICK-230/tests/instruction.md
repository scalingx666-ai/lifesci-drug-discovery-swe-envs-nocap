# Issue

**Title:** Rolling back to old anlytical sswder code

## Description

In this PR, I have made necessary change to disable numerical grid weight derivatives and enable old analytical implementation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `20b593bc81ef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
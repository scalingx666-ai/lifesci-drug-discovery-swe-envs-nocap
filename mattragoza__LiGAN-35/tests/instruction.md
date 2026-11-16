# Issue

**Title:** Suppress ob warnings

## Description

For some molecules, openbabel will generate a large number of error/warning messages. When using weights and biases, which captures/reports the stderr, these error messages can cause a deadlock that brings training to a halt. This deadlock is avoided by suppressing error and warning messages from openbabel, which is what this PR does.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df7a6fc05310`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Increase keywd length

## Description

Match API keyword string length to Amber.
Increase from 200 to 256.
Longer is better to prevent truncation e.g. with long libxc functional names etc.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9a2e4aaf9bbd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
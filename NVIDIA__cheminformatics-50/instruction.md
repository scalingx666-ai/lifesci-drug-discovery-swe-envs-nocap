# Issue

**Title:** Security bugfix: NGC Security Scan failure...

## Description

Upgrade libssl and openssl.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b36de969369a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
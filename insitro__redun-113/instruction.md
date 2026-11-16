# Issue

**Title:** Fix context file read from s3

## Description

Addresses #112 

cc @wfondrie 

Use redun's `File` class so that we can support context files from any redun-supported file system.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07704565bea8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
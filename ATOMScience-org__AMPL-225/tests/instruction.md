# Issue

**Title:** updated the model file reader

## Description

- Use  tarfile.open() instead of tempfile.mkdtemp() 
- Added a function to process multiple tar.gz files

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `556fcd3573e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
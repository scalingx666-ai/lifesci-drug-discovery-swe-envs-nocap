# Issue

**Title:** Add env.sh script.

## Description

Script could be used to setup env vars. No need to hardcode path in ~/.bashrc
Will export full path regardless the CWD:
`. ../EAS_NI/env.sh`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `207be1fa9a4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
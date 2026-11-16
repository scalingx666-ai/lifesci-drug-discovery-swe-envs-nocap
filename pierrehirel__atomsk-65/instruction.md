# Issue

**Title:** fixed a few issues with installation src/Makefile

## Description

Installation of atomsk to a custom path failes if some folders are missing.
1) added INSTPATH to the CONFPATH variable
2) added creation of BINPATH folder same way as others are created

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1dac885b4f58`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix cmake imported target files

## Description

They where missing the INTERFACE_INCLUDE_DIRECTORIES property for some reason.

Fix #251

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6bed1848760c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
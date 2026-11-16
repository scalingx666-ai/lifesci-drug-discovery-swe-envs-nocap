# Issue

**Title:** lock emsdk version

## Description

It seems like we can't build with v7 of emsdk (which is what latest now resolves to).

temporarily lock the version to 6.0.13 until we can fix that.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3332794bb2ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** staging, update flake.lock

## Description

Problems to fix:
*  [x] Python2 has finally been removed from upstream.
   cleanup all remaining Python2 packages and artifacts.
* [x] Ambertools, fixes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d761af4dc02b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
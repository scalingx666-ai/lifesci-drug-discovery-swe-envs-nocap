# Issue

**Title:** molpro: 2024.3.0 -> 2025.4.1

## Description

https://www.molpro.net/manual/doku.php?id=recent_changes

The "socket" communication scheme has been removed. The new and only supported version is now molpro-pr.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59b01ab5cdb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
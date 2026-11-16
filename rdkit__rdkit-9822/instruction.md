# Issue

**Title:** Fix thread safety in conformer tracking

## Description

Different bits had been written separately, but were not technically safe due to the underlying datatype being shared between thrads

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4cdcc848adfa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
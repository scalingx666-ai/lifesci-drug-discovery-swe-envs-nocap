# Issue

**Title:** add overload for ROMol addHs in combination with addHsParameters

## Description

This overload was missing, as discovered by @DavidACosgrove 

Implements it the way I've seen it in other places.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fbb0f798a5d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
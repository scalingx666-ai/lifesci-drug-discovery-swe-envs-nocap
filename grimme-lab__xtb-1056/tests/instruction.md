# Issue

**Title:** Increase number of characters for Schoenflies notation from 4 to 6

## Description

Applies the fix suggested in #593 which should help with #1052. This should allow Dinfh and Cinfh symmetries.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67a6b3b8b418`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
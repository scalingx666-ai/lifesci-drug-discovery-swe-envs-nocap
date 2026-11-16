# Issue

**Title:** Fixes #9757

## Description

This .

I added a check to `getStereoInfo(Bond)` to look for consecutive double bonds on atoms with an effective valence of 4, and in such cases, do not identify the bond as a stereo double bond.

The test can most likely be improved, but this one seems to work well enough. Suggestions are welcome.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78ee45e0d2df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
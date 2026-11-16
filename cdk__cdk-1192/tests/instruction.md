# Issue

**Title:** Fix some corner cases in reading of stereochemistry from chair projec…

## Description

…tions. Some chairs may be drawn with horizontal bonds the interpretation of which depends where on the ring we are.

We now pass in the central point of the connected ring atoms to know which way (up or down) we should assign the atom. We also improve the interpretation of angled chairs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ffa903da9e44`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
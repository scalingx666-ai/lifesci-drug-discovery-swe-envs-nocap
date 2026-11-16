# Issue

**Title:** LargestPiSystemDescriptor visited flags and minor code improvements

## Description

Makes LargestPiSystemDescriptor use an internal "visited" array instead of the IChemObject flag VISITED of the atoms for safe parallelisation over shared molecule instances.
Also, minor code improvements in exception handling and un-commented debug messages (and added a logger to the class, first of all).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e9145c3270e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
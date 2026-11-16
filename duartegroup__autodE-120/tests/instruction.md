# Issue

**Title:** Allow G profiles with association complexes

## Description

Adds a configuration flag to enable free energy profiles when association complexes are also calculated – not sensible so off by default but available for those that are feeling brave. Suggested by Thijs – thanks for the suggestion 😄

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fcd2834ee8ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
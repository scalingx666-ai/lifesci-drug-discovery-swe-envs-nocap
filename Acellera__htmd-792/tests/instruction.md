# Issue

**Title:** Fix Gasteiger charges

## Description

- [x] Implement `fitChargesWithAntechamber` (not used now, but it is left for AM1-BCC option)
- [x] Guess bond type if needed
  - [x] Implement `guessBontType`
- [x] Fix #789
- [x] Update tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07533e780346`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
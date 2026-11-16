# Issue

**Title:** Repulsion fix

## Description

- return atomwise repulsion from `get_engrad`
- add general tests and tests for position autodiff
- improve type hinting

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `86babe822441`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
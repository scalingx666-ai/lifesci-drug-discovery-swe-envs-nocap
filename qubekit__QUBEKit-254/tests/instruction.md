# Issue

**Title:** More Improper torsion tests.

## Description

## Description
This PR adds some more tests for improper torsions to make sure none are lost when round-tripping to file after parameterization. This extends the last test as the number of improper torsions is explicitly checked rather than the total energy as they may not contribute much when relaxed.

## Status
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9d8c5de48e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Molpro: Writing the multiplicity

## Description

- Changed how multiplicity is set in the Molpro input file so it is actually used by the program. 
- The previous way of setting was never used by the program (a default guess was used instead)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d9f2283885a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
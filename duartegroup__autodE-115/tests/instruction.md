# Issue

**Title:** MOPAC input fix 🐞

## Description

Fixes a bug found while investigating #114 where the maximum number of optimisation cycles in the input keywords was not considered thus an extraneous number was added to the input, causing MOPAC2016 to crash with constrained optimisations. This PR fixes this by skipping any MaxOptCycles keywords in the input

***

- [x] Run examples with MOPAC + ORCA

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3cc7eaad2f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
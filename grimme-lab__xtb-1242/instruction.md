# Issue

**Title:** Increase maximum number of arguments for `rdblock`

## Description

Number of comma-separated values for, e.g., `$thermo` `temperatures` entries was limited to 24. Since this does not really affect the total `xtb` memory consumption, I'd just increase it to prevent issues like in #1158.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a91c8ac63554`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
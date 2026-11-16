# Issue

**Title:** Prevent inconsistent multiplicities

## Description

- prevent inconsistent multiplicity and charge (number of electron) assignment by terminating the calculation
- wrong printout as described in #1107 is also avoided
- CAUTION: Breaks support for getting results for any calculation setup and expects the user to define a chemically reasonable input.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41059b44d84a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
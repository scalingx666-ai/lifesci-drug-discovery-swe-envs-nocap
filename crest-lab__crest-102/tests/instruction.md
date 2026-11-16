# Issue

**Title:** Update of topology check

## Description

The topology check now allows specification of atoms to exclude from the comparison.
Command: `--notopo <X>`, where `<X>` is either the number of the atom(s) in the input file or the element symbol. E.g. `--notopo 1,5,10-14` or `--notopo Fe,O`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5044e7501096`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
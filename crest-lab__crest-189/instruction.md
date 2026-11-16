# Issue

**Title:** Introducing flag for extensive QCG grow search

## Description

- The QCG citation link was corrected.
- A new Flag for the QCG grow algorithm was introduced. The '-normdock' flag employs the aISS algorithm with normal settings and not with faster settings as before. This leads to a more extensive search for solute--solvent interaction sites but increases the computational costs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97a9867b9676`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
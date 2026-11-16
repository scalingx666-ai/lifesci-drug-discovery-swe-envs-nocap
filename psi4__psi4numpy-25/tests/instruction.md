# Issue

**Title:** Added a SAPT0(ROHF) example.

## Description

## Description
Added an example for open-shell SAPT0, SAPT0(ROHF). The induction and exchange induction energy is calculated without response (which is exactly what Psi4 can do at this time).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ecd54472ba3b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
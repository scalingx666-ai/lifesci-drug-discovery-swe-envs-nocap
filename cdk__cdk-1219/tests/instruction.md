# Issue

**Title:** Fix a corner case with titles for reactions not being set if no CXSMI…

## Description

…LES layers were present.

Minor fix, some reaction titles from SMILES were missing

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b80f90e42d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
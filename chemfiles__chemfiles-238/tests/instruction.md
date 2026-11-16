# Issue

**Title:** Fix PDB atom type issue

## Description

There's a problem in how the atom type in PDB files was being read. This leads to a confusion between CA (as in alpha-carbon) and Ca (as in calcium). Below is a quick fix.

Previously, the additional test failed as the mass of an alpha carbon was 40!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7480bf7447cd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
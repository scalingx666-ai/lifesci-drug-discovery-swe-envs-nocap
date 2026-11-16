# Issue

**Title:** Improvements for PDB reader

## Description

This PR should fix the following two issues:
 Hydrogen detected as Hahnium
 Reading resnames starting with zeros

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71607eba68ba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
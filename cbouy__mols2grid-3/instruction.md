# Issue

**Title:** Directly using an RDKit mol with the `mol_col` parameter

## Description

Added an option "mdl_col" to use coordinates allready present in DataFrame or other input. There are probably other ways to implement this, but I needed a way to draw molecules with the coordinates prepared in advance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3d5101ecc44`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
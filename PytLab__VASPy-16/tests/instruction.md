# Issue

**Title:** Correct scripts/xdatcar_to_arc.py

## Description

Use `xdatcar.atom_numbers, xdatcar.atom_types` instead of `xdatcar.atoms_num, xdatcar.atoms`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3650b3e07bcd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
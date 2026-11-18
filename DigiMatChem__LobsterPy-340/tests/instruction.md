# Issue

**Title:** Update get struct path

## Description

# Changes

1. Update the `get_structure_path `function to also check for POSCAR.lobster.vasp files in the calc directory
2. Rename one of the POSCAR file to mimic such a scenario

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f883b246c35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Added changes to OpenFF parametrisation to better handle system excep…

## Description

…tions; fully? documented file_handling.py; stopped ligand params being changed when unnecessary (name, topology, atoms); cleaned imports.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fab55b248b53`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
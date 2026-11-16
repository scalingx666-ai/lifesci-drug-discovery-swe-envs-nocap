# Issue

**Title:** Misc fixes

## Description

- Fixed a bug in reading PDB X coordinate

- Fixed a bug in reading PDB residues

- Fixed a bug when a MOL2 file does not begin with @TRIPOS<MOLECULE>

- Added support for SDF charges

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d289e7b37035`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
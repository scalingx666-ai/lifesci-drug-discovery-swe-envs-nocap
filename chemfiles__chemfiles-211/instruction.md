# Issue

**Title:** Additional PDB fixes

## Description

The purpose of this PR is a few fold:
 - [X] Fix issue #207 
 - [x] Fix issue #210
 - [x] Add secondary structure information stored in PDB/MMTF files.
 - [x] Read frame properties from PDB files, like `HEADER`, `TITLE`, etc.
 - [x] Add corresponding properties from mmCIF and MMTF where applicable.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21dfdd37f87c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
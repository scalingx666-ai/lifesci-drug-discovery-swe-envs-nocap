# Issue

**Title:** Fixes error in 2D depiction due to RDKIt update

## Description

- Fixes 2d depiction bug
 - Uses RDKit functionality without coordgen library for 2D depiction

Updated version number and changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81f3c9ed8dc2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
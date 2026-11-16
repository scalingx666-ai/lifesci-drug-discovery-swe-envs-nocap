# Issue

**Title:** Moved initialisation of PSI4 to only when it is used; added clean-up …

## Description

…of lig.chk and lig.fchk files; prep'ed for LJ updates

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d151232159b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
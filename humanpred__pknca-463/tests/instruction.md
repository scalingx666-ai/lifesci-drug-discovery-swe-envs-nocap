# Issue

**Title:** Add new urine parameters: VOLPK, renal CL norm by Dose

## Description

This PR:

* Defined parameter calculation for total urine volume (`volpk`) and its tests
* Introduced dose-normalized renal clearance parameters (`clr.XXX.dn`...) and registered its units

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb70375d5c51`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Better subprocess handling

## Description

- PaDEL's native timeout functionality causes some compounds to "hang" during calculation
    - for higher-level functions, from_smiles and from_mdl, supplied timeout now controls subprocess.Popen's timeout instead of PaDEL's

This change reduces the chance of a compound to fail during calculation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93c25aa65c79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add option to select solvent model to the C-API

## Description

Addresses  (and partially ) 

This adds a parameter to `setSolvent_api` to allow it to also set the solvent model used. Depending on concerns about API stability, I could make a new `setSolventWithModel_api`.

In addition, a convenience method is added for running CPCM-X calculations. This handles running both the SCF loops.

New API tests were added for the ALPB, COSMO, and CPCM-X solvent models.

Results object now stores a solvation energy, accessible through `xtb_getSolvationEnergy`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec4f3887e143`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix frcmod writer

## Description

There was an issue in the frcmod writer because it was not respecting the AMBER format. In case of single letter atom types it needs to add a space after the atomtype. This tripped off tleap which read wrong parameters for the impropers from the frcmod and caused some wrong energies. Very reliable these MD file formats :laughing:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0483702573df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
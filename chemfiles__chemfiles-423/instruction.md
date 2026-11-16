# Issue

**Title:** PSF reader based on VMD molfile

## Description

Temporary solution to #208.

~This is based on top of #422, which contains changes to the VMD molfile code, I'll rebase once it has been merged.~

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96f2332213ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
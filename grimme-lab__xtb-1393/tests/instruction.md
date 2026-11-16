# Issue

**Title:** Increase width of coordinates in Cosmo files

## Description

* Previously any coordinate -100 bohr or smaller, 1000 bohr or larger would fail to be written. This increases these limits to -1000 and 10000 respectively.

Misprinted coordinates would break the parsing in downstream code like CPCM-X if the coordinates dipped below -100 bohr.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d44803e2c0b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
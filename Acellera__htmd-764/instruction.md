# Issue

**Title:** Set box size in tleap for CRD files

## Description

Added the command to set the box size.
As a consequence I found out we did not read correctly CRD files when they include box sizes at the end and fixed that bug.
Had to update all test files since tleap moves all coordinates to the positive domain when setting a box size. Also for some reason the tleap log now suddenly prints out the PDB resid instead of it's internal resid. Weird stuff but it seems to work correctly.

Closes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `60bb1e4ccf36`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
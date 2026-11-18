# Issue

**Title:** Fix atomic radii parameter used in SG1 grids (Z > 18)

## Description

Previously the SG1 atomic radii (R) in QUICK were the following:

1. For Z=1 to 18 (H to Ar) the values were taken from Table 1 of _J. A. Chem. Phys. Lett. 1993, 209, 506_
2. For Z>18 all R were set to 2.25 au.

This PR fixes the R values for Z>18 by computing values directly from the work of Slater, _J.C. Slater, Phys. Rev. 36 (1930) 57_. The location of maximum of the radial charge density (R) for the outermost shell is obtained by `(n*)^2/(Z-s)` where n* is the effective principal quantum number of the outermost shell (not equal n for n > 3) and s is the screening constant (value depends on the type of shell and number of electrons).

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aad51ed5d7dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
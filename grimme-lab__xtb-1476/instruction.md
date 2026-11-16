# Issue

**Title:** Restore the original GFN1-xTB 5s/5p basis expansion

## Description

The STO-NG basis set expansion for the 5s/5p shells (In-Xe valence) for GFN1-xTB (and IPEA-xTB) was changed in #157 to the Stewart expansion from 1970. The original 6.2 release of xtb used the segmented contraction with shared s- and p-functions by Pietro et al., Inorg. Chem. 20, 3650, 1981. However, the parametrization was never adapted to this. tblite actually uses the Stewart 1970 expansion also for the 4s/4p shells (Ga-Kr).

The important change in #157 was moving from using the `SETSTO6` function (old Pietro values) to using the `slaterToGauss` path.

It is not really clear which expansion is the right one, but since the original 6.2 release used the shared sp version, I suspect this was also used during the fit. @awvwgk do you remember why you changed this (Stefan cannot remember doing a refit of GFN1 in 2020)? If this wasn't an intended change at the time, I would revert this to the original version (I prepared a PR for tblite as well to enable this choice). 

This prepares the long-term switch to using tblite for all Hamiltonians by fully aligning the xtb and tblite SCF results. The remaining difference comes from Cutoffs and the Angstrom-to-Bohr conversion (adapted soon)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d7cac2eb117`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
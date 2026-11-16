# Issue

**Title:** Fix mSVP basis-function count in GCP parameters

## Description

The GCP parameter table for the mSVP basis used an incorrect number of basis functions for part of the modified Ahlrichs DZ + def2-SV(P) definition. This caused the GCP correction to be overstated for mSVP and for the 3c methods that derive from it.

- Corrected the `nbas_msvp` entries in the GCP parameter table so the first transition-row counts match the actual basis function count.
- Updated the affected regression/reference energies for the mSVP and PBEh-3c-based corrections to reflect the corrected basis definition.
- Kept the scope limited to the incorrect parameter data and the corresponding expected values.

```fortran
! modified Ahlrichs DZ, supplemented by def2-SV(P)
integer, parameter :: nbas_msvp(*) = [ &
   & 2, 2, &
   & 9, 9, 15, 15, 15, 15, 15, 15, &
   & 15, 18, 18, 18, 18, 18, 18, 18, &
   & 24, 24, ...
]
```

<!-- START COPILOT CODING AGENT SUFFIX -->

-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `730c44b0e8dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
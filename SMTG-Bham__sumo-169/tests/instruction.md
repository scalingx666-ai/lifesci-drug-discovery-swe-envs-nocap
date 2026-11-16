# Issue

**Title:** Fix k-point indicies in sumo-bandstats

## Description

The pymatgen logic for extracting branches in the band structure requires duplicating the high-symmetry points. To avoid wasting compute resources on these extra points, sumo-bandplot/bandstats adds this points dynamically rather than including them in the DFT calculation.

However, this means `sumo-bandstats` reports the wrong indices for the VBM and CBM with respect to the band structure calculation. This PR fixes this behaviour.

Fixes: #167

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a7e44f0d91a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
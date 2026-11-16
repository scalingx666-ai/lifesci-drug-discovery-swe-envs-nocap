# Issue

**Title:** fix(tng): Correct Conversion of Length Units

## Description

At the moment only the box is converted from nm to angtrom. However all length dependent units should be converted. Especially positions and velocities.
Furthermore TNG does not always use nm. In fact one could specify an arbitrary exponent for length units. This is handled by these changes.

Relevant GROMACS source: https://github.com/gromacs/gromacs/blob/ac628532b96f338ace10fb78a01d47e109b81bb8/src/gromacs/fileio/tngio.cpp#L1258-L1283

**TODO:**
 - [x] update tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d289e7b37035`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
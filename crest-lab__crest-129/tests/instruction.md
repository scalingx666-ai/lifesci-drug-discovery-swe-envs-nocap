# Issue

**Title:** Added rr-ho interpolation for heat capacity in thermo.f90

## Description

The RR-HO interpolation is performed for *S*<sub>vib</sub> (<https://doi.org/10.1002/chem.201200497>).
As per communication with S.G., the same type of interpolation *should* also be conducted for *C*<sub>p</sub>.
This implementation does that. Only a very minor change that doesn't affect anything else.
For `--sthr 0` the "original" *C*<sub>p</sub> without interpolation is correctly recovered.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `20827d163581`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
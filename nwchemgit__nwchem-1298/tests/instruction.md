# Issue

**Title:** Use python3 for integer conversion scripts

## Description

The 64_to_32 and 32_to_64 wrapper scripts invoke the converter with
`python`. On systems where Python 3 is installed as `python3` but no
`python` command exists, the conversions fail.

For `64_to_32`, these failures can be particularly difficult to diagnose:
the converter processes run in the background, the missing `python`
commands do not cause the wrapper to return a failure status, and the
`64_to_32` make target subsequently creates its completion stamp even
though the source conversion did not occur.

This resulted in an NWChem build using 8-byte default Fortran integers
calling the 32-bit BLAS/LAPACK interface directly. A simple H2 SCF
calculation then failed in geometry processing with:

    geom_binvr: dsyev failed

Change both conversion wrappers to invoke `python3`, consistent with the
Python 3 converter scripts.

Tested with GNU Fortran 13.3.0 and OpenBLAS:
- `make 64_to_32` completed successfully and converted BLAS/LAPACK calls
  (for example, `dsyev` to `ysyev`).
- NWChem built successfully with `BLAS_SIZE=4`.
- H2 STO-3G SCF completed successfully with total energy
  -1.116759310275.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4baf01cc18be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
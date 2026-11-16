# Issue

**Title:** Transformed cube

## Description

Promolecular Transformation of a Cubic grid class. This is regarding issue #15.

Functionality
----------------
- Transform Cubic Grid in [0,1]^3 to R^3 using promolecular.
- Transform individual points.
- Integration (has weak tests).
- Jacobian of Transformation.
- Steepest-ascent of a function in Theta space.
- Directional derivatives in Theta space (Not Tested). 
- Instead of [0,1]^3, change to [-1, 1]^3 and in docs (a35a07e).
- Added dynamic bracketing (b8fc2b2).
- Added Cubic Grid as Tensor Product of OneD grids (c104ac6).
- Added tolerance and using masked arrays for integration (eb32897). 
- Hessian of transformation (9e73400)
- Interpolation and Derivative Interpolation (8727c0a).
- Python dataclass is not in py36 (187c00e).

TODO
---------
- Make/Reduce tests faster
- Vectorize Logarithm Interpoaltion
- Test for Directional Derivative.

May 16, 2023. All of the TODO except for the "Directional derivative tests" are now fixed/added.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f45b334ceec7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
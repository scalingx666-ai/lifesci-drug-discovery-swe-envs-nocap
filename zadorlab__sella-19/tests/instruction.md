# Issue

**Title:** Add external Hessian function calculation to Sella

## Description

This PR accomplishes a few goals:
1) Provide a means by which to evaluate Hessians using an external program, e.g. exact analytical Hessians
2) Fix the issues we have previously experienced when converting Cartesian Hessians into internal coordinates
3) Add keyword to the Sella optimizer to control how frequently the Hessian is diagonalized/evaluated

Specific changes:
- Add a keyword argument `hessian_function` to the `Sella` class. This optional keyword accepts a function that takes an ASE Atoms object and returns a numpy array containing the Hessian matrix in a Cartesian coordinate basis and in units of eV/Angstrom^2. Providing a value to this keyword overrides the default behavior of constructing the Hessian matrix internally; instead, the Hessian will be calculated with the provided function (and converted to internal coordinates as needed).
- Add a keyword argument `diag_every_n` to the `Sella` class. This optional keyword accepts an integer that indicates how often the Hessian should be evaluated. Providing a value to this keyword overrides the default behavior and forces a Hessian evaluation every `diag_every_n` steps (internal logic may result in the Hessian being evaluated *more* frequently, but never less frequently).
- Adds internal helper functions to the `InternalPES` class `_convert_cartesian_hessian_to_internal` and `_convert_internal_hessian_to_cartesian` which do what the name indicates. I hope to extend this to be used when the internal coordinate system must be reconstructed due to one or more internal coordinates becoming invalid (which would be an improvement over the current behavior of simply throwing out the Hessian entirely).

TO DO:
- ~~Make sure the code runs~~ Done
- ~~Test in Cartesian coordinates~~ Done
- ~~Test in internal coordinates~~
- ~~Test with ML potential from the Head-Gordon group~~

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db56c4147989`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
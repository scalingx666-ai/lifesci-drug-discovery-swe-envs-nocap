# Issue

**Title:** Preserve fixed points when copying force fields

## Description

`OptimizeMoleculeConfs` with multiple threads copies the supplied force field, but the copy constructor omits fixed-point indices. Consequently, atoms marked with `AddFixedPoint` can move during optimization.

Copy `d_fixedPoints` alongside the energy contributions. Add regressions covering independent fixed-point lists, rebinding copied fields to separate coordinates, and UFF/MMFF optimization with 1, 2, and 4 threads. Threaded results now preserve fixed coordinates and match serial results.

Validation:
- Six native CTest targets passed.
- All 22 Python helper tests passed using RDKit 2026.09.2 with the patched constructor preloaded.
- New regressions fail with the original constructor and pass with the fix.

AI assistance: implementation and tests were prepared with OpenAI Codex.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c686c2c945df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
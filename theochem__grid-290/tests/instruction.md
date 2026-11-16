# Issue

**Title:** Fix cubic file unit detection for negative dimensions

## Description

This PR fixes the unit detection logic in `UniformGrid.from_cube`. 
As discussed in the issue, there is a discrepancy between the Gaussian documentation and observed behavior:
- **Documentation**: States `N1 < 0` implies Bohr.
- **Observed (dx2cube)**: Generates files with `N1 < 0` that are in Angstroms.
- **Observed (cubegen)**: Generates files with `N1 > 0` that are in Bohr.

This PR aligns the reader with the observed behavior of tools like `dx2cube` and `cubegen`:
- `N1 < 0` → **Angstrom**
- `N1 >= 0` → **Bohr**

**src/grid/cubic.py**: Updated `UniformGrid.from_cube` to set `unit='angstrom'` when `shape0 < 0`.
**src/grid/tests/test_cubic.py**: Added `test_read_negative_shape` to verify that negative dimensions are correctly interpreted as Angstroms.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41c57c929b82`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
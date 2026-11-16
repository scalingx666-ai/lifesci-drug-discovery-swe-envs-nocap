# Issue

**Title:** Add: export Matrix::swap_columns and Matrix::sort_cols

## Description

## Description

`Matrix::swap_columns` and `Matrix::sort_cols` exist in C++ (`matrix.h:1033`, `:1037`) but are not exported to Python, while the neighbouring `scale_column` and `rotate_columns` are. Reordering MO columns from the driver currently needs an element-by-element `get`/`set` loop.

## User API & Changelog headlines

- [x] `psi4.core.Matrix.swap_columns(h, i, j)` and `psi4.core.Matrix.sort_cols(sortvec)` are callable from Python. `sortvec` is a `psi4.core.IntVector` with one permutation per irrep.

## Dev notes & details

- [x] Two `.def` lines in `export_mints.cc`, next to `scale_column`. `IntVector` is already bound.

## Questions

- [x] None.

## AI

- [x] AI assistance: spotting the missing bindings, code, description.

## Checklist

- [x] No test: bindings over existing C++ methods.
- [x] Docstrings are in the export.

## Status

- [x] Ready for review

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f67d6ea5eafd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
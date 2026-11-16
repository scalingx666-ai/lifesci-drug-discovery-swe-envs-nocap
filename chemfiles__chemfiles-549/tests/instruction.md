# Issue

**Title:** Preserve explicit CML coordinate origins

## Description

Preserve explicit zero-valued coordinates when reading CML. Coordinate fields
are selected by attribute presence rather than by whether their values are
nonzero, so a fractional origin or 3D origin no longer falls back to alternate
coordinates.

 and #541.

The regression test covers fractional, 3D and 2D origins. The complete local
CMake/CTest suite passes: 295/295 tests (macOS, Apple Clang, Release build).

This repair is part of our previously disclosed study of chemistry software.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `582e6da1ce7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
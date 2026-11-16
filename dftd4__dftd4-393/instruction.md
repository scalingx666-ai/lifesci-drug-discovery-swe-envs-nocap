# Issue

**Title:** Enable building Python API with CMake

## Description

This adds CMake support for building the Python API and addresses #380:
- Add the `DFTD4_WITH_PYTHON` option for building the Python extension as part of the main CMake project.
- Add a standalone `python/CMakeLists.txt` for building the CFFI extension against an in-tree, installed, or bundled dftd4 library.
- Document the corresponding CMake build procedure.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `30c5b8187c25`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
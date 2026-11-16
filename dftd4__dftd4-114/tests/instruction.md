# Issue

**Title:** Update dependency handling logic in meson and CMake

## Description

- allow meson to find dependencies before falling back to subprojects
- add custom CMake finder for mctc-lib, mstore, multicharge and BLAS
- add CMake macro to find (cmake/pkgconf) or include (subproject/fetch) dependencies
- BLAS finder export respective targets for older CMake versions

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `82f55ccc90b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
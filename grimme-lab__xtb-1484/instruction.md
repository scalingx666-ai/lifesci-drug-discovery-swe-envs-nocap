# Issue

**Title:** CMake cleanup

## Description

- Move CMake setup and options into the top-level file so configuration is easier to find by users.
- Replace `WITH_OBJECT` and separate static/shared targets with one library controlled by `BUILD_SHARED_LIBS`, making the standard option effective and removing duplicated logic.
- Apply compiler options and feature definitions through targets so xTB-specific settings do not leak into dependencies.
- Remove `INSTALL_MODULES` option and always install the C header and Fortran modules, making both interfaces available to downstream users. Keep the module installation directory configurable through `CMAKE_INSTALL_Fortran_MODULES`.
- Use only `find_package(LAPACK REQUIRED)`, which also handles BLAS, to avoid redundant discovery and linking.
- Rely on `GNUInstallDirs` defaults for target installation and remove redundant output/include settings to simplify the rules while preserving configurable paths.
- Export a consistent `xtb::xtb` target and resolve enabled dependencies in the package configuration so downstream usage works for both library types.
- Drop build-tree exports, including the manual mctc-lib export, to maintain only the installed package interface.
- Switch default build type to `Release` so default builds prioritize performance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `920a35fb5126`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
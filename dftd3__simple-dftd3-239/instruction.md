# Issue

**Title:** CMake: Add SDFTD3_INSTALL_FMODDIR

## Description

This is mainly for convenience of Fedora packaging as it requires Fortran modules to be installed under `%{fmoddir}`.

Note: We shouldn't simply adopt what's done for mctc-lib etc:
```cmake
set(
  "${PROJECT_NAME}-module-dir"
  "${PROJECT_NAME}/modules"
  CACHE STRING
  "Subdirectory to install generated module files to"
)
set(
  module-dir
  "${${PROJECT_NAME}-module-dir}"
)
set(module-dir "${module-dir}" PARENT_SCOPE)
```
Downstream sets `CMAKE_INSTALL_INCLUDEDIR` to `%{_lib}/gfortran/modules` as a workaround, which is not applicable to s-dftd3 as it has public C header. This is also an issue on dftd4 and tblite side; will fix them soon (update:  ).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5bf48d73c493`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
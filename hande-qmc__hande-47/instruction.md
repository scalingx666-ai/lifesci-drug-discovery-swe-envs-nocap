# Issue

**Title:** CMake: HDF5 detection and update docs

## Description

- Update building with CMake docs.
- Modify the way the `--hdf5` flag works. It now accepts a path to a custom compiled version of HDF5 and internally sets `HDF5_ROOT`. This is then similar to the way `--lua` works, which is less confusing for the user. **Note** setting `LUA_ROOT` and `HDF5_ROOT` as environment variables achieves the same effect as using the configuration script flags (according to CMake docs and my tests, at least)
- The compatibility check between HDF5 and Fortran compiler now logs its output to a file upon failure. This should help the user debug the problem or at least provide more complete information to the developers.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bdaf5d7858ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
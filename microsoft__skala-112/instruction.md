# Issue

**Title:** Fix native example builds in clean environments

## Description

## Summary

Fresh conda environments exposed several implicit native linking and CMake configuration assumptions in the GauXC and FTorch examples.

This PR:

- links the C GauXC frontend with the C++ linker driver so transitive C++ dependencies such as LibTorch are included
- enables C and C++ before Fortran so CMake selects matching conda compiler wrappers
- disables upstream GauXC test executables in release builds, while retaining validation through Skala's integration examples
- creates FLAP's generated module directories before CMake validates their exported include paths
- adds a relocatable `$ORIGIN/../lib` install RPATH to the FTorch executable

Environment caching was already disabled on `main`, so every Examples job continues to solve and build from a clean environment.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `35dd9b91b6b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
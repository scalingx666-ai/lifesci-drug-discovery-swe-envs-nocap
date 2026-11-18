# Issue

**Title:** GitHub CI Workflow Enhancements Part 4

## Description

This PR expands the Github CI workflow-based tests to cover multiple architectures, OS versions, and compiler versions using the public Github runners:

- Legacy configure/Makefile builds:
  - Ubuntu 24.04 (x86_64): GCC (v12.3.0, v13.3.0, v14.2.0)
  - Ubuntu 22.04 (x86_64): GCC (v10.5.0, v11.4.0)
  - Ubuntu 24.04 (Arm64): GCC (v14.2.0)
- CMake builds:
  - Ubuntu 24.04 (x86_64): GCC (v12.3.0, v13.3.0, v14.2.0), Clang (v17.0.6, v18.1.3)
  - Ubuntu 22.04 (x86_64): GCC (v10.5.0, v11.4.0)
  - Ubuntu 24.04 (Arm64): GCC (v14.2.0), Clang (v18.1.3)
  - MacOS 13 (x64_64): GCC (v14..2.0_1 via Homebrew), Clang (v15.0.7 via Homebrew)
  - MacOS 14 (ARM): GCC (v14..2.0_1 via Homebrew), Clang (v15.0.7 via Homebrew)

The above legacy/CMake combinations are used for testing both serial and MPI QUICK versions.

Notes / Limitations:
- Legacy configure/Makefile builds do not support Clang.  An initial attempt at adding support was made but later aborted (Fortran preprocessor issues for Linux runners; empty symbol errors for static libraries created via ranlib for MacOS runners).  Future work can add this support if necessary.
- Several Fortran compilation issues were encountered with this expanded testing (mainly type mismatches in scalar/array routine arguments).  These issues, which were primarily in the DL-FIND Fortran interface, have been monkey-patched so that all tests are now passing.  However, this work may need to be revisited if issues surface.

Ideas for future enhancements:
- Add tests for Windows Github runners (e.g.,  [windows-2022](https://github.com/actions/runner-images/blob/main/images/windows/Windows2022-Readme.md)). 
- Add tests for additional compilers (Intel legacy & LLVM-based).
- Add tests for even older GCC/Clang versions (for common server/LTS linux/unix distros).  There is an Ubuntu 20.04 Github runner, but I was trying to be reasonable with the number of jobs being launched for testing different configurations (256 jobs is the max. limit).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15eaf51dcdc0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
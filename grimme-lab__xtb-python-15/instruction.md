# Issue

**Title:** Add OSX support

## Description

OSX support for the C-API has not been tested up to now, so there is no guarantee for it to work at all.

Tested so far:

- clang (XCode 11.5 + gfortran-8 from homebrew, default-library=static) fails to link
- GCC 7.5.0 (homebrew, default-library=static) fails unpredictable with segfaults
- GCC 8.4.0 (homebrew, default-library=static) does not pass tests
- GCC 7.5.0 (conda-forge, default-library=shared) fails unpredictable with segfaults

Due to lacking physical access to a Mac this is quite hard to debug and has therefore rather low priority. Any contributions to this effort are more than welcome.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1cf3ef20b876`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
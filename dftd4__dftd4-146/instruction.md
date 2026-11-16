# Issue

**Title:** pin fetched dependency versions in cmake build

## Description

I noticed that when mctc-lib, mstore and multicharge are fetched, cmake always fetched the head of the repository.

This patch adds some code to pin the fetched dependencies to the same versions specified in dftd4/subprojects/*.wrap

This helps make automated builds more reproducible, although it would be desirable to centralize versions in a single central file, or at least set them up as global CMake variables.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d8ef7ad9242`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
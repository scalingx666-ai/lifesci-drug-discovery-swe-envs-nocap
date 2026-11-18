# Issue

**Title:** CMake Updates for AmberTools and CUDA v13.2.1

## Description

This PR contains CMake updates backported from recent AmberTools 2026 (rc6), along with improved version check support for CUDA v13.2.x builds.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5446219cf8b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
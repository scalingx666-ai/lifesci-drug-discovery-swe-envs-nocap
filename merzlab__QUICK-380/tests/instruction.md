# Issue

**Title:** Update Github CI workflows for CPU builds and tests

## Description

This MR updates the QUICK tests in Github workflows to use v4 artifact actions  (v1 and v2 deprecated, then removed -- see [here](https://github.blog/changelog/2024-02-13-deprecation-notice-v1-and-v2-of-the-artifact-actions/)).

Additionally, this MR also updates the checkout action (v4), renames the build artifacts to avoid naming conflicts between the two build systems (legacy configure/make, and CMake)., parallelizes the serial builds, switches to invoking the CMake build/install commands directly (instead of depending on the generated Makefiles), and refactoring the general job and step naming to better reflect the tasks.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d6cf2d4e0b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
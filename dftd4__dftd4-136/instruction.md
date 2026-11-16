# Issue

**Title:** Update dependency handling in meson

## Description

Some code simplification in the build system to allow better caching of dependencies in superbuilds

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `270d31ba0f11`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
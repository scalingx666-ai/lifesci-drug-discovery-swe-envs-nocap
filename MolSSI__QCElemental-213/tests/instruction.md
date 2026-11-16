# Issue

**Title:** CI: Non-matrix products builds

## Description

<!-- Thank you for your contribution! -->

## Description
Attempts to use non-matrix product builds. Previously everything in the matrix would simply build the Cartesian product unless some trickery with excludes was used. This uses a `cfg` yaml config found by @jaimergp.

## Changelog description
N/A

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a47be4ae373e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
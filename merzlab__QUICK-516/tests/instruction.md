# Issue

**Title:** macos-14 tests updated to macos-26

## Description

GitHub retired all macOS 14 runner images on November 2, 2026. This PR switches macos-14 testing with macos-26.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `03f44a36f2bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
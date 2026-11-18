# Issue

**Title:** AWG Updates to infos

## Description

Updates README, program header, and CMake version info.
- Version is now 24.03
- Support f functions
- HIP currently disabled, available in 23.08 but not 24.03
- Supports macOS ARM
- Ask to cite geometry optimization paper

@Madu86 I do not know how to update links to documentation. Links are set to point to version 23.08. This needs to be updated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3c7dab21b6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
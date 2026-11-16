# Issue

**Title:** Enable compatibility with C++14 and Qt 5.14+

## Description

- Conditionally use back-ported template specialization
- Replace depcreated timer class
- Bump required language standard to C++14 to avoid warning (errors) with more recent CUDA toolkits than CUDA 9 (caused by Thrust)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34a06d8341bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
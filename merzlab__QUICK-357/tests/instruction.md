# Issue

**Title:** AWG - fix reading heavy elements

## Description

Support reading as many elements as are defined in quick_constants_module. These are 92 elements. We do not have ECPs so there are not really any basis sets that we can use beyond Kr. However, at least be consistent for the future.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3188d58823dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
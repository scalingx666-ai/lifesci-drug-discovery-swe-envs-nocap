# Issue

**Title:** Update to PseudoPotentialIO 0.3

## Description

About damn time! I wonder if we should validate that the parsed file is a `UpfFile`. And we could also support `Psp8File`s if we wanted to.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91aff12eca25`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add a condition to fix nan in noble gas atoms #100

## Description

1. For most atoms, if nan given, automatically select
atomic radius with 1 less.
`warning`: No.86 RN will still be broken.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e8b473c3ec1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
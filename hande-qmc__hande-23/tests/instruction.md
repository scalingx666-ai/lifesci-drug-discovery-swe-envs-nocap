# Issue

**Title:** Generate git_info.f90 and print_info.c at build time with make

## Description

Previously we were generating them at configuration time instead -- this
is a (undesired) change introduced when adding cmake. cmake already
produces these files correctly at build time.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aecc4031813e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
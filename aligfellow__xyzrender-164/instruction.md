# Issue

**Title:** Honor manual TS bonds in vibration GIFs

## Description

Adds manual transition-state bond selection to vibration GIFs. When `--ts-bond` is used with `--gif-ts`, the selected bonds replace the automatically detected TS bonds. The same option is also available through the Python API.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d2029dda1f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
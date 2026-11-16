# Issue

**Title:** Update .readthedocs.yml

## Description

Documentation builds were failing with

```
Error

Config validation error in `build.os`. Value `build` not found.
```

This PR updates the `.readthedocs.yml` file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f250c3ecd880`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
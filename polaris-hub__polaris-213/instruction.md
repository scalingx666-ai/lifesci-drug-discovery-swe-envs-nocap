# Issue

**Title:** Fix: Exclude some computed properties during caching

## Description

## Changelogs

- Computing the zarr checksum manifest properties during caching would fail. We thus exclude these properties from the `model_dump()`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff4ca357c079`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
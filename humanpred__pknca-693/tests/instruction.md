# Issue

**Title:** review: tidy the registry-cache tests and notes

## Description

Drop the unused pk.nca() result assignments in the registry test, restore
the registry in the requires test with local_interval_cols() so the
derived store and sort order are reset too, wrap the NEWS bullet at 80
characters, and say in the classification notes that set_requires_inputs()
caches outside the registry.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `191c27ac7583`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
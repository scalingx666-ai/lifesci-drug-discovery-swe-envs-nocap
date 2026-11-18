# Issue

**Title:** Add T008-T010 updates from t011-base branch to master

## Description

## Description

We have fixed issues with T008 and T010 (and updated T009 according to changes in T008) in PR  Since this PR will not be merged for quite some more time, let's add the updates for the "old" notebooks already now to `master` (T008 and T010 are _not_ running).

## Todos

Please refer to issue  for a detailed description of the `pypdb`-related issues in these notebooks.

Summary:
- T008 and T010: Use `biotite` instead of `pypdb` to query PDB IDs matching a list of criteria
- T008 and T010: Restructure theory part to include `biotite` _and_ `pypdb`
- T009: Rerun with new structure in T008

## Questions

None.

## Status

- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9bdb38b53b9e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
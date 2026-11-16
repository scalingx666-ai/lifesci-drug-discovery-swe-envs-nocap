# Issue

**Title:** Ability to add entries to a singlepoint dataset from other datasets

## Description

## Description

Adds the ability to create entries in an existing singlepoint dataset from completed calculations in an optimization dataset, or from entries in another singlepoint dataset.

For an optimization dataset, you will specify the optimization dataset, as well as the specification to pull the completed records from. Then, entries will be added to the singlepoint dataset, where the `molecule` of the entry is set to the `final_molecule` of optimizations.

This will only use optimizations with a `complete` status. Existing entries (with the same name) will not be overwritten in the singlepoint dataset, so it should be safe to run incrementally (ie, run periodically as more calculations finish in the optimization dataset).

For a singlepoint dataset, you will only need to specify the dataset, and entries will be copied over.

## Status
- [X] Basic functionality
- [x] Better metadata return (just counts)
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e6f3f39450c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
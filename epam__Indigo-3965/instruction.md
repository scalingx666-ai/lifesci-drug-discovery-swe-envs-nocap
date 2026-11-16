# Issue

**Title:** #3957 – Molfile V3000: FIELDDATA on a non-data S-group crashes the loader

## Description

## Summary

Loading a V3000 molfile in which a non-data S-group (GEN, SRU, SUP, ...) carries `FIELDDATA` crashed the process: the value was written through the null `DataSGroup` pointer.

`FIELDDATA` on a non-data S-group is now skipped, like the neighbouring data-only keys `FIELDNAME`, `FIELDINFO`, `QUERYTYPE` and `QUERYOP`.

## Tests

- Core: `IndigoCoreFormatsTest.mol_loader_v3000_fielddata_on_non_data_sgroup` — GEN, SRU and SUP S-groups with `FIELDDATA` load, the keys and S-groups after it are read, and a V3000 round trip keeps them.

## Generic request
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name does not contain '#'
- [x] base branch (master or release/xx) is correct
- [x] PR is linked with the issue
- [x] task status changed to "In Review"
- [x] code follows product standards
- [x] regression tests updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dffe6bb47227`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
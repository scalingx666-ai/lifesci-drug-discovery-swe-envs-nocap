# Issue

**Title:** Sanity check number of basis functions in get_reference_hdf5.

## Description

This check is already performed in read_restart_hdf5 but that happens
after get_reference_hdf5 and, if the sanity check doesn't hold, a rather
confusing error message resulted.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5793c2e30ebe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
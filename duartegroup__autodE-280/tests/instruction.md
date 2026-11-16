# Issue

**Title:** DHS code improvements

## Description

- Changes trust radius for optimiser to 0.1 Angstrom (since default step size for DHS is also 0.1 angstrom, anything larger does not make sense)
- Replaces `left_coord` and `right_coord` properties of the image pair object with `left_coords` and `right_coords` to match with other parts of autodE.


***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [x] Documentation has been updated
* [x] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f9fb7a0e733e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
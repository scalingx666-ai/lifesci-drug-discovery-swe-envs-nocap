# Issue

**Title:** Remove clearance_hepatocyte_az dataset with duplicate entries

## Description

## Summary
- Removes the `load_clearance_hepatocyte_az` dataset loader and all references
- The dataset contains 1213 entries but only 1020 unique SMILES, with conflicting labels for duplicated molecules
- This is a known upstream TDC issue (mims-harvard/TDC#356)

Removed from: loader function, `__init__.py` exports, benchmark mappings, dataset name lists, tests, and Sphinx docs.

## Test plan
- [ ] Verify no remaining references to `clearance_hepatocyte_az` in codebase
- [ ] Existing tests for other datasets still pass
- [ ] `load_tdc_benchmark` and `load_tdc_splits` work without the removed dataset

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `839001468ba8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
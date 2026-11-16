# Issue

**Title:** Fix fetch validation failing on a single empty example row

## Description

## Summary
- `_validate_csv` in `standard_example.py` was failing the whole fetch as soon as **one** of the 3 fixed example rows (from `run_input.csv`) produced empty output, instead of only when **all** rows are empty.
- This contradicts the policy already correctly implemented in `checks.py`'s robustness check (fail only if all sampled rows are null), and was causing working models to be rejected and auto-deleted at fetch time due to normal per-molecule variability.
- Found while investigating fetch failures for `eos633t` and `eos3kcw` in ersilia-os/ersilia#1810 — both models are fine; `eos3kcw` had 2/3 valid example rows when it failed.

## Test plan
- [x] Verified against a captured real failing output (eos3kcw, row 3 empty, rows 2 & 4 valid): now returns `True` instead of `False`
- [x] Verified an all-empty-rows CSV still correctly returns `False`
- [x] Ran `test/cli/test_fetch.py` and `test/cli/test_serve.py` — no new failures (one pre-existing unrelated failure on master, confirmed via git stash)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6e504c3dd48`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
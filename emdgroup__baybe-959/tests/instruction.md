# Issue

**Title:** Fix pending experiment exclusion in discrete recommendations

## Description

### Summary

Preserve candidate identities when excluding pending experiments.

### Details and comments

`Campaign.recommend` merged discrete candidate rows with pending experiments, producing a fresh `RangeIndex` and potentially multiple rows per candidate. That indexed merge result was OR-ed with metadata carrying the original candidate indices and applied as a positional filter, so supported `SearchSpace.from_dataframe` inputs with sample IDs could return a pending experiment again (even with `allow_recommending_pending_experiments=False`) or raise `NotEnoughPointsLeftError` although valid candidates remained.

The fix replaces the merge-indicator Series with exact joint-row membership over consistently ordered discrete parameter columns, yielding one positional boolean per candidate regardless of sample index or duplicate pending rows. Existing measured/recommended/excluded metadata restrictions are combined unchanged; off-grid/tolerance behavior and rejection of empty pending dataframes are untouched.

Adds regressions covering string/named/reordered numeric indices, duplicate pending rows, the allow-pending flag, nonmatching pending data and mixed categorical/numeric row matching.

Verified locally: `pytest -q tests/test_campaign.py` 72 passed; ruff/format/flake8/pydoclint pass on changed files.

AI-assisted implementation; I supervised and checked the work as it progressed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b838c9cf7af3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
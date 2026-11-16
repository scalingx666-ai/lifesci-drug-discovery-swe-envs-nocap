# Issue

**Title:** Fix tests for pytest 8

## Description

Fix #100. Additionally, takes care of the following `pytest` warning:

```
  /Users/romeli/mambaforge/envs/spyrmsd/lib/python3.11/site-packages/_pytest/mark/structures.py:357: PytestRemovedIn9Warning: Marks applied to fixtures have no effect
  See docs: https://docs.pytest.org/en/stable/deprecations.html#applying-a-mark-to-a-fixture-function
    store_mark(func, self.mark)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8d3c540c2f6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** pd.append -> pd.concat

## Description

**Problem:** Pandas `append` has been deprecated since version 1.4 and has been removed since version 1.6. `create_group_split` still uses `pandas.append` to split the train_val set into the train and val sets.

**Solution:** Updates `create_group_split` to utilize `pandas.concat` to create the train and val sets.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e656c5316dcc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
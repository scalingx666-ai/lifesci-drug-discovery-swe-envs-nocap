# Issue

**Title:** chore: correct cddd sample file and notebook

## Description

There were some rows with NaNs for all the CDDD columns: the molecules were not CDDD-compliant.

I didn't catch the error in my notebook, since I am using a very recent version of scikit-learn, that doesn't crash on NaNs.

Now the sample file includes rows without NaNs. I also reexecuted the notebook.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2973f70f58ea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
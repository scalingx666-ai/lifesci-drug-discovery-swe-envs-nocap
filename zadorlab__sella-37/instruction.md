# Issue

**Title:** Use keyword argument names in `Optimizer` `__init__`

## Description

.

All sella optimizer classes are no longer functional with ASE as of 10 hrs ago due to https://gitlab.com/ase/ase/-/merge_requests/3287. The root cause of the problem is that sella calls the `__init__` of the `Optimizer` class without explicitly specifying keyword argument names (i.e. by supplying all arguments as positional); however, some keyword arguments were just removed from the ASE `Optimizer` class, resulting in a mismatch between the expected and actual arguments being passed. This PR fixes the behavior by writing out the keyword argument names as needed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a4afee529cd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
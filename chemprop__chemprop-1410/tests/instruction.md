# Issue

**Title:** Fix bond constraint

## Description

Right now, for atom/bond property prediction, only constraining atom predictions to sum to a value, or only bond, does not work.  When I wrote the code originally I thought the relevant variables would be empty lists, but they are actually None. Two possible fixes are to change their default to an empty list, or to add a check if the variable is None. I opted for the later to avoid introducing other potential bugs. 

I tested this by first adding a test and verifying it fails. Then I added the fix and the test now passes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db0bb86fbad6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
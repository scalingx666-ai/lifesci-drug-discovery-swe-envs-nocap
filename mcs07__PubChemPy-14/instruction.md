# Issue

**Title:** fix #13 check if identifier is None and raise an exception to let the user know that the identifier is invalid

## Description

I had a bug and the original error confused me a lot.
I understand that checking invalid input types in python does not make sense in a duck typing sense, however the case for None I think it needs to be checked.
Feel free to close without merge.
I think that the original bug is on get_compounds that returns a cid as None.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9de4f2cca694`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
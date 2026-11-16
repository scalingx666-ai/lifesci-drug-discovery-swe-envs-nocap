# Issue

**Title:** rework gpu typing

## Description

Remove protocols that were only used by one class. 

Introduce dtyping for arrays and shape typing for numpy arrays as well, where it was easy. 

Also simplified the include mechanism for gpu a bit more. 

Updated to new gpu4pyscf interface and used dataclasses instead of NamedTuple

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad23cf0b3451`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
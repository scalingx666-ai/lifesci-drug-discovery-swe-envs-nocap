# Issue

**Title:** multiple architectures can be provided to CMAKE through -DQUICK_USER_…

## Description

The architectures are provided as per following for 2 or 1 architectures.

-DQUICK_USER_ARCH="ampere;hopper"
or
-DQUICK_USER_ARCH="ampere hopper"
or
-DQUICK_USER_ARCH=ampere

Note: the code generation for multiple architectures will take significantly longer.

*** The user manual needs to be updated ***

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc80f985f714`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
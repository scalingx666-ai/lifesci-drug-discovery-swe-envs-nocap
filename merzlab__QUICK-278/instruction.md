# Issue

**Title:** AWG: Remove redundant hard-coded SCF DIIS exit condition

## Description

The exit condition `idiis.gt.MAX_DII_CYCLE_TIME*quick_method%maxdiisscf` is 1) redundant in the current implementation and 2) leads to a hard-coded maximum number of SCF iterations (DIIS subspace size times hardcoded number of maximum DIIS iterations). This is dumb, also because `idiis` is always equal `jscf`, hence it is sufficient to check for `jscf` as exit condition to limit the number of SCF iterations.

Here we remove the redundant condition and get rid of unnecessary `MAX_DII_CYCLE_TIME`. The user can choose the number of SCF iterations and size of DIIS subspace. There is no need to limit the number of DIIS cycles.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e03bb293db47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
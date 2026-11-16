# Issue

**Title:** Fix GCC-15 build

## Description

This patch fixes build for GCC-15 (both gfortran and gcc). All xtb tests were passed.

Only symmetry_i.c was affected with `int true(void) { return 1; }` function. I have renamed it as `verify_point_group`. Other changes are related to warnings (`-Wall -Wextra` for AppleClang and `-Wall -Wextra -Wno-comment` for GCC-15) and some reformatting.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09288659551c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
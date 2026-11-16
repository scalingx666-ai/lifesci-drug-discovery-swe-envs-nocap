# Issue

**Title:** Fail for keyword used with wrong delimiter

## Description

Replaces the misleading warning for specification keywords that were dropped before. Any keyword previously using `=` instead of `: ` was either ignored with a warning or even silently. Meanwhile, the user expected the keyword to be read in [src/constrain_param.f90](https://github.com/grimme-lab/xtb/blob/c1e244be5c504dc06a9a9a388da48873a27b87cd/src/constrain_param.f90#L338).

I now raise clear errors if a keyword is used with the wrong delimiter.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c1e244be5c50`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
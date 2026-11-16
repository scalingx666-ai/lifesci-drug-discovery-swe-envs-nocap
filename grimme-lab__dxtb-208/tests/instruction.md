# Issue

**Title:** Disable timer by default

## Description

Timer will now be disabled. Can be enabled globally, by setting the environment variable `DXTB_TIMER=1` or, for the calculator, by passing `timer=True` as keyword argument during instantiation of the calculator.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b31746425ae2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
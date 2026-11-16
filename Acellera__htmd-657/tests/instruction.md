# Issue

**Title:** change tutorial tests to only run tests starting in test_tutorial

## Description

This is just a bug fix, without the permanent solution yet.

My experience with the test_tutorials function is that pytest is not only collecting the 2 test functions we have, but also the `from htmd.ui import *` at the top of each file. This is the work around I found, by using the -k argument: it still collects them, but it does not run them.

This fix makes my release job easier, as it reduces release time from ~ 5 hours to ~ 1 hour.

There was no issue associated with this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `616d188e58a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** make gfn0 builtin

## Description

GFN0 had the problem that its parameters were always read from the external parameter file and no finished built-in variant existed which caused problems if the xtbpath was not set. This PR elevates this problem.

The tests are not super pretty for the testing if built in parameters are the same as the one from the external parameter file, despite using testdrive. there is also an issue open regarding this problem at testdrive #

Once this is closed one can change it here or get rid of the tests as the parity has been established with this PR

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `920a35fb5126`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
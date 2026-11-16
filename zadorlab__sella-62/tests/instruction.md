# Issue

**Title:** Fix broken tests, add guards to divide by zero, minor other bugfixes

## Description

I did some static analysis of the code to look for bugs and found a number of places where divide by zeros could occur. They are addressed in very light touch ways here, and mostly serve to point them out to you in case you want to address in a more intelligent way than just flooring to tiny numbers.

The analysis also turned up some minor other bug fixes. Also I fixed the broken tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f8b21d67700`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
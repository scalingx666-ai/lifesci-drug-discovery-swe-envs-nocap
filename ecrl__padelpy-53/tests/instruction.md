# Issue

**Title:** Fix Incompatibility with Python 3.12

## Description

According to the Python docs for the random module ([here](https://docs.python.org/3/library/random.html#functions-for-integers)):  

`Changed in version 3.12: Automatic conversion of non-integer types is no longer supported. Calls such as randrange(10.0) and randrange(Fraction(10, 1)) now raise a TypeError.`

Python 3.12 will no longer automatically cast these floats to ints, making padelpy incompatible with 3.12. This patch should fix it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b992b47ad54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Parmed 3 fix

## Description

This makes HTMD compatible with parmed 3+ but breaks compatibility with parmed 2.7.
It will not pass the tests here since we would need to update parmed on acellera channel but I tested it locally and it passes all tests. 


As per this issue I had to implement improper center detection to be compatible with the new way it stores impropers.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e30ddd04a66`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
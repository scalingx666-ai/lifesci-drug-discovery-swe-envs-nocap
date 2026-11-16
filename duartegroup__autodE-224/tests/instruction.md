# Issue

**Title:** Fix cleanup with null filename

## Description

##  

Note: with the example in #223 there is now no exception thrown, but I don't think any files are actually deleted 😕

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `696e1b02513a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Return approximate total matching results

## Description

The number returned is using folded fingerprints, so it's not entirely accurate, hence the 'approximate'.

This commit is more unpleasant than I had hoped because we have to pass the results up and down so many call stacks.  If only we had a result class object....

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52c6463894a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
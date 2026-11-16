# Issue

**Title:** broken links

## Description

cc:  @garrison 
- Removing a link that no longer exists from v0.11 release notes (lmk if there is a better link to use rather than removing it)
- Testing what happens with the single underscore vs. double, since the link did not translate properly through our pipeline

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08678a478b66`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
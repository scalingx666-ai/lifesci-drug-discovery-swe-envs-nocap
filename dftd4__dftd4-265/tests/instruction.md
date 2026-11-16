# Issue

**Title:** Update the CI

## Description

I updated the CI comparably to the tblite based fully on pip. I removed also the build and python yamls for micomamba. 

Now the full CI including coverage and wheels works again.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7fa3ccfd6442`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
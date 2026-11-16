# Issue

**Title:** Allow Python 3.13

## Description

Allows Python 3.13 installation, fixes  I ran tests locally and everything seems to be working.

I also changed the version to 1.2.7, since that would probably be the next release, but I can revert that one if necessary.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f2acb44a016`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
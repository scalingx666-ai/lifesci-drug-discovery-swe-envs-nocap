# Issue

**Title:** Fix a segfault in SMI reader

## Description

While I was at, I also changed the few remaining tests using boost::fs to loop over 'bad' files, and found one case of broken error message.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd4f20e8953b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** make sure only parent proc writes to shared arrays

## Description

Hi, so hopefully this will help eliminate race conditions with the one and two body arrays for integral storage.
@andreeaf would you mind running this quite a few times on Jenkins since this has flagged up the race condition problems?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0cd750354e5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
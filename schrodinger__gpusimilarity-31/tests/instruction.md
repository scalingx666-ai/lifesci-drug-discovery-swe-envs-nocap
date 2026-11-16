# Issue

**Title:** Add similarity cutoff, refactor 'all' search from python to C++

## Description

In order to handle the on-GPU filtering of similarity, it necessitated moving multiple database ('all') searching into C++.  At this point that's probably the better move anyway, the reason it was in the python was that single binaries didn't know about all databases until recently.

The good news @greglandrum !  Using basically any level of on-gpu similarity filtering dramatically speeds up the algorithm.  For instance, if I set a 0.5 similarity cutoff with 128 bit fingerprints on GPU (but still full-fingerprint screening of initial results on CPU, so same results back), I'm seeing screening speeds of ~2-3 billion compounds a second!  This is because I cut off everything below 0.5 before doing the indices sort, which is the most expensive part of small fingerprints.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb140d8e18c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
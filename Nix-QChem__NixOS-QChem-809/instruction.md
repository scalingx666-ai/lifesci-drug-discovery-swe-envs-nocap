# Issue

**Title:** libefp: remove

## Description

The libefp repository for Psi4 has been removed and consequently libefp does not build anymore, unless you get the sources from our cache. Then again, Psi4, the only *previous* consumer, does not use it anymore, so I've just removed it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27973a6fa10a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
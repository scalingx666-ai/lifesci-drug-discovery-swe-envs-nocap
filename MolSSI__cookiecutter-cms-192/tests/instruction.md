# Issue

**Title:** Minor version 10 being miscast as .1

## Description

This turns the CC version into a string so that X.10 does not get converted to X.1 in print. This would happen with X.20 but not X.11 or X.25 for example.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1bc7ecc991f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
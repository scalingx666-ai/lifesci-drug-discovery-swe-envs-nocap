# Issue

**Title:** Fixed missing -Ds from defs in mkconfig.py.

## Description

Manually changing the #defines has got lost somewhere along the way

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c18969e38c1a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
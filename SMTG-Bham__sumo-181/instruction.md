# Issue

**Title:** Fix projected band plot with 2 colour

## Description

Changed the defaults of colour1, colour2 and colour3 from red, green, blue to red, blue, green to make it easier to reproduce the expected behaviour with 2 colours.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52e219065de9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
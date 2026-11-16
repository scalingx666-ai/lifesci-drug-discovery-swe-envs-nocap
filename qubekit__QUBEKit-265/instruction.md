# Issue

**Title:** Clean-up of non-bonded and better logging of info

## Description

Removed old chargemol.py.
Temporarily fixed -display.
Added message showing error in esp for each atom during virtual site fitting.
LJ now able to use alpha/beta from FB output.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `87c890c1bb07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
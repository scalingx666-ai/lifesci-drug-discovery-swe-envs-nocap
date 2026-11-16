# Issue

**Title:** Pin python dependencies in setup.py

## Description

A recent Click update (version 7.0) broke a simple unit test (added a new output line). Also `matplotlib==3.0` dropped Python 2 support. We pinned the latter to the latest LTS version, and the former to version 6.7.

Also pinned some other python packages that made sense.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd1374742934`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
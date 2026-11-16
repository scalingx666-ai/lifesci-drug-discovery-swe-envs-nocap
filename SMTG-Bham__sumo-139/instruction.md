# Issue

**Title:** Fix xmax typo in optics_plotter

## Description

Noticed this typo when getting some absorption plots with sumo, where the CLI-specified xmax would be overridden by the automatic value. Tested and fixes the issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c331ba6b62a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
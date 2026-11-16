# Issue

**Title:** Modified picking information

## Description

This doesn't fix any bug but adds some information to the dictionary returned by picking; crucially (for me), which component the item belongs to. In addition, if an item is clicked twice, NGLWidget.picked is changed each time.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9a8206709de5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
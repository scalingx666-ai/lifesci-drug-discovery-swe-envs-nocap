# Issue

**Title:** Fix saving of plots

## Description

plt.show() was called before the files were saved which resulted in white plots.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `696c53d155cc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
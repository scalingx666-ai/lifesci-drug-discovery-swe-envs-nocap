# Issue

**Title:** Support unnamed molecules

## Description

As noted in #79, e3fp requires that molecules have the property `_Name` even if we don't need that. Since we only need that just for saving, this PR changes the behavior to throw an error if `_Name` is needed and otherwise to proceed as normal.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4fea3d6c3460`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Update readme

## Description

and #301

# Changes

1.  Consistent CI and package dependencies
2. Removed redundant pytestify from ci
3. Restructure readme > move dev installation below normal installation
4. Pin numpy to `numpy==1.26`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55d8d2e119aa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
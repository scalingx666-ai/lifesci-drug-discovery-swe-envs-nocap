# Issue

**Title:** fix: Issue with Numpy version requirement from fastpdb/biotite

## Description

# Description

This PR pins the Numpy version to 1.x.y, to match the requirement from Biotite, itself required by FastPDB. On a clean virtual env install, the Numpy 2+ raises an error when importing Polaris.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e23c4a1c4491`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
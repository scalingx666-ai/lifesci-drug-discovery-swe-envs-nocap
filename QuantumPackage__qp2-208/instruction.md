# Issue

**Title:** CSF-CI Open-Shell debugging

## Description

This PR fixes the following:
1. [x] Open-shell CSF to Det conversion
2. [ ] Prepare for CFG-CI #187 
3. [ ] Prepare for SO MEs #184 
Testing is required.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `727815751cdc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix bug in Velocity Verlet

## Description

## Description
@pwborthwick recently pointed out that the Velocity Verlet code had "0*5" instead of "0.5", which led to incorrect behavior. The print statement also was not consistent with Python3.

## What are your new additions? Please provide a brief list.

* **Changes**
  - [ ] Fix typo in Velocity Verlet code
  - [ ] Change `print` statements to be python3 consistent 

## Status
- [ ] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09f5e8163afb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
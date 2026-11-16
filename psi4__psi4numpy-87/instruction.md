# Issue

**Title:** Update MP2.py

## Description

The SCS-MP2 correlation energy was printing the SS-MP2 correlation energy.
A simple variable switch was performed in line 104:
print('\nSCS-MP2 correlation energy: %16.10f' % SCS_MP2corr_E)
instead of,
print('\nSCS-MP2 correlation energy: %16.10f' % MP2corr_SS)

## Description
Please provide a brief description of the PR's purpose here.

## What are your new additions? Please provide a brief list.
* **New Features**
  - [ ] Feature1
  - [ ] Feature2

* **Changes**
  - [x] Change1  

## Any questions for the community?
- [ ] Question1

## Status
- [ ] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `32000df910ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
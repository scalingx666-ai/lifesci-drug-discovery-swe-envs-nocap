# Issue

**Title:** Correction to QED-CIS

## Description

## Description
The additional diagonal contributions to the bilinear coupling in QED-CIS should cancel. This is also wrong in the publication, which has already been discussed with the author and will hopefully be taken care of soon.

## What are your new additions? Please provide a brief list.
* **New Features**
  - [ ] QED-CIS is correct now

* **Changes**
  - [ ] Deleted terms, which should cancel anyway, but leave a nuclear dipole contribution in the previous implementation.
  - [ ] Corrected corresponding test 

## Status
- [x] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c6a78ff5244`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
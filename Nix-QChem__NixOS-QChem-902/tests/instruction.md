# Issue

**Title:** Fix fallout from latest staging merge/gcc-16 update

## Description

Currently broken are:

* [x] bagel
* [x] neci
* [x] et
* [x] dftbplus

Broken upstream:
* [x] ergoscf 
* [x] tblite 
* [x] elpa 

CC @sheepforce

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b94577876f50`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
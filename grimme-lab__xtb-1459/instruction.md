# Issue

**Title:** Fix ALPB and GBSA kernels in tblite interface

## Description

Switches the kernels for ALPB and GBSA consistently with the paper, so ALPB now uses `p16` and GBSA uses `still`. Internally, tblite and the native xtb implementation already use the correct kernel.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0aadb4360076`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
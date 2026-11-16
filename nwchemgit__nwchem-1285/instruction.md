# Issue

**Title:** fix COSMO util_print handling

## Description

Moved util_print_pop call to avoid conflict with theory prints.  
Prior to this fix, theory print/noprint options (e.g. DFT) were ignored when COSMo is present

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `86b193cfeb2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
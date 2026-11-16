# Issue

**Title:** Nao import

## Description

When NAO are used, some functions in QP try to access the GTO basis, e.g. to calculate the AO kinetic energy or nuclear potential matrices. This PR mitigates this by providing reasonable substitutes to avoid trying to calculate these values and completing the fake internal GTO basis.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5543cb37a8a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix for issue 212

## Description

It turned out that temporary arrays used for ERI code dont have enough host memory when they are allocated. I was using 4GB per core; but 2 processes would require ~10 GB. Ive reorganized the code to delete host arrays as soon as they are allocated but this is pretty stupid. We should update templates to make dev only allocations in future. Will do that in a separate PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1ddcd1f79bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
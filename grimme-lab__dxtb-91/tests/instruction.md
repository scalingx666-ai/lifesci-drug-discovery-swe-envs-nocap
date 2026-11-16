# Issue

**Title:** SCF without full gradient tracking (cleanup)

## Description

Run the SCF cycle inside a torch.no_grad() context and perform an extra iteration with gradients afterwards.

Reference gradients are obtained with tblite.

Currently, the gradients for torch.double are not within our common threshold (sqrt(torch.finfo(dtype).eps) * 10) but only exact up to around 1e-6. For larger systems, the deviations are larger (up to 1e-2).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `095635f73634`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
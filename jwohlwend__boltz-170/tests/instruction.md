# Issue

**Title:** mmcif: scale qa_metric.PLDDT to [0,100]

## Description

This follows what was already done for B-factors in 

It seems to be the convention to have those values in [0,100] rather than [0,1].
E.g, this is useful when visualizing the structure with `mol*`, as it would automatically apply an appropriate pLDDT colorscheme:

Before:
![before](https://github.com/user-attachments/assets/bff7dd4f-8361-40d7-8213-c67bb33ec483)

After:
![after](https://github.com/user-attachments/assets/8da13e1e-8a86-436d-98a3-a5b2d24d6c98)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `80b9fe6c349a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
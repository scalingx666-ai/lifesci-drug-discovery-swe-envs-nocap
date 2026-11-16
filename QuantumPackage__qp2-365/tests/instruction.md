# Issue

**Title:** Fix segfault in scf

## Description

Evalutating ( (j<=mo_num).and.(fock_matrix_diag_mo(j)-fock_matrix_diag_mo(i) < 1.d-5) ) cause a segfault with gfortran compiler as soon as j > mo_num, the two conditions must be evaluated separately.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c6d513bbf12`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
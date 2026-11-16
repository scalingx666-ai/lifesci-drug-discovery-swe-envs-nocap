# Issue

**Title:** Fix wrapping kpoints at -0.5/0.5

## Description

Enforce that the kpoints to be wrapped between [-0.5, 0.5), as the previous code may generate both -0.5 and 0.5 due to finite precision. This is achieved by check if the wrapped point is close to 0.5 (<1e-7). If so, it will be changed to -0.5.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb6fb44a55cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
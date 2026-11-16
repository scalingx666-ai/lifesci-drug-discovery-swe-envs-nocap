# Issue

**Title:** Fix L-ANC with fragmented Hessians and fixed atoms

## Description

Exact atom fixing determines the reduced optimizer dimension independently of fragmented Hessian selection. Give it precedence so large GFN-FF optimizations request the number of modes left by the fixed-coordinate projection.

Since we have the exact fixing take precedence, we also skip the fragmented eigenvector mean adjustment when exact fixing is active, since it causes nominally fixed atoms to drift.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b31754bf3c7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
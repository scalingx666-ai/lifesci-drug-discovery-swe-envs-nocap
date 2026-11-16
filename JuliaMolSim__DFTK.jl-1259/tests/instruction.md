# Issue

**Title:** Use AD to compute xc kernels

## Description

Key insight: Kernel application is just a Hessian-vector product, which is typically done with forward-over-reverse. We already write the gradient by hand, so to get the kernel we don't need to use reverse mode and we can just do a push-forward with ForwardDiff. This already just works for DftFunctionals, and this PR also implements the necessary rules for Libxc lda and gga.

In my testing this is 1-2x slower than writing the kernel by hand, but it does require less code, and will extend trivially to mgga!

TODO:
- [x] Does this work on the GPU?
- [x] Nothing is testing that the derivative of `e` (energy per unit volume) is correct.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `11b584675927`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Guard against FP underflow

## Description

For systems with coordination numbers much larger than the largest reference coordination number, the norm in the calculation of the Gaussian weights can become tiny. This can trigger floating-point underflows that lead to essentially random values. This also made the correctness depend on the compilation settings (ifort with -O3 was correct, -O0 was incorrect).

We now guard against tiny norms and set problematic cases to zero.

Related:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb004c8d23cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix bugs handling time-reversal symmetry

## Description

There are two problems with the previous implementation:
- the reduced mapping must be generated without time reversal symmetry, otherwise the k = K + G_0 does not hold. 
- The C_k(G) = C_{-k}(-G) must to honoured to get the correct spectral density when summing up coefficients.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e0c113b89304`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix flicking xtb/gfnff test

## Description

This patch fixes flicking gfnff test that sometimes happens on MacOS runners due to out-of-memory access. 

As I can see, there should be an additional term related to topology constraints, however, it was never implemented for gradients.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6eb6720a341`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
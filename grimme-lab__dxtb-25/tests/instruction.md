# Issue

**Title:** Automatic differentiation for repulsion

## Description

- autodiff of repulsion energy w.r.t `alpha`, `zeff` and `kexp`
- tested with `torch.autograd.gradcheck` for single and batch
- replaced `Geometry` object with `numbers` and `positions` (as suggested by @awvwgk)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ab3bfbc4e48`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Remove redundant hankel dispatch

## Description

Case already covered by https://github.com/JuliaMolSim/DFTK.jl/blob/38d2c2e906f34243b812273d45f238564173512b/src/common/hankel.jl#L12-L15

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38d2c2e906f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
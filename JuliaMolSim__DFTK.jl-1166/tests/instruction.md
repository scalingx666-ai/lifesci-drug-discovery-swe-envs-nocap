# Issue

**Title:** Fix DivideAndConquer in Julia 1.12

## Description

Julia 1.12.0 is now used by the "Julia latest" workflow in CI even though no announcement was made yet (see https://julialang-s3.julialang.org/bin/versions.json).

Turns out that `DivideAndConquer` is not exported, so we need to prefix it by `LinearAlgebra.`. The `>= v"1.12"` check is false for pre-releases, which is why this only started failing now.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8b8f4b75477`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Make SCF runs optionally reproducible by providing a seed

## Description

We had a discussion wrt. randomness before, and the conclusion was that we should keep DFTK random by default but allow passing a seed for reproducibility[^1]. It seems that the best way to achieve this in Julia is to seed the `TaskLocalRNG` since any subtask will be seeded from it automatically. This takes care of the multithreading aspect and makes the required changes minimal.

Additionally, the scfres now contains a seed that can be used to reproduce the run[^1].

If this is satisfactory @mfherbst I am happy to implement the same approach for the other solvers (direct minimization etc) as well. For tests, it should be sufficient to just seed the task local RNG before each test; I haven't looked into it yet though.

[^1]: Assuming the exact same Julia and packages versions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d012b7c00ee4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
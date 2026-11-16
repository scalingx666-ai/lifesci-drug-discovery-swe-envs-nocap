# Issue

**Title:** Fix Anderson on GPU

## Description

The PR fixes the Anderson acceleration on GPU. Errors were triggered because of `M = @view M[:, 1:end .!= idrop]`, where `1:end .!= idrop` produces an array of Bool (which is not appreciated as indexing by GPU arrays).

Note that the error was only obvious on AMD GPUs. However, it also sometimes happened on NVIDIA GPUs too. It is not clear to me why the issue arises more often on some hardware. It is possible to trigger the error with high probability by changing the value of  [maxcond](https://github.com/JuliaMolSim/DFTK.jl/blob/79d911cf40c08ff474e76f324bcadf83bbe874f3/src/scf/anderson.jl#L42), e.g. by setting it so `1e-2`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79d911cf40c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
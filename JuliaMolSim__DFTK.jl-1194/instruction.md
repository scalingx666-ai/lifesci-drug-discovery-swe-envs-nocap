# Issue

**Title:** Utilities to estimate RAM usage

## Description

Adds a `estimate_memory_usage` utility function to estimate the memory usage. It can be computed without instantiating the terms in the basis. The results are also printed when displaying the `basis`.

Example, for a simple silicon run:
```
    Estimated memory usage (per MPI process):
        nonlocal projectors  :   3.2 MiB
        single ψ             : 634.4 KiB
        single ρ             : 210.9 KiB
        peak during SCF      :   7.4 MiB
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6ab012465385`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Print Mem_DF memory even if Disk_DF selected

## Description

When running HF/DFT computations with default settings, the MemDFJK algorithm memory estimate is now printed under the Integral Setup header even if the program eventually selects DiskDFJK. This way, users can easily see how much memory a computation would need to run fully in core. 

**if MemDFJK selected:**

```
==> Integral Setup <==

  DFHelper Memory: AOs need 21.009 GiB; user supplied 58.019 GiB. 
  SCF_SUBTYPE=INCORE selected. In-core MEM_DF algorithm will be used.
  Using in-core AOs.

  ==> MemDFJK: Density-Fitted J/K Matrices <==

    J tasked:                   Yes
    K tasked:                   Yes
    wK tasked:                   No
    OpenMP threads:              10
    Memory [MiB]:             59411
    Algorithm:                 Core
    Schwarz Cutoff:           1E-12
    Mask sparsity (%):      56.9419
    Fitting Condition:        1E-10
```

**if DiskDFJK selected:**

```
==> Integral Setup <==

  MemDFJK Memory: AOs need 21.009 GiB; user supplied 11.256 GiB.
  MemDFJK requires too much memory. DiskDFJK algorithm will be used.

  ==> DiskDFJK: Density-Fitted J/K Matrices <==

    J tasked:                  Yes
    K tasked:                  Yes
    wK tasked:                  No
    OpenMP threads:             10
    Integrals threads:          10
    Memory [MiB]:            11526
    Algorithm:                Disk
    Integral Cache:           NONE
    Schwarz Cutoff:          1E-12
    Fitting Condition:       1E-10
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a264c0517ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
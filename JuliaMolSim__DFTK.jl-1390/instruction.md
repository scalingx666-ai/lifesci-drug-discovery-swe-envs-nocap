# Issue

**Title:** GPU optimization of G vector unique norms

## Description

When doing GPU stress calculations of large systems, a new bottleneck arises: `PlaneWaveBasis{Dual}` instantiation of xc, local, and nonlocal terms. Substantial work has already been done to speed up the integration on the pseudopotential grids (#1262, #1265), which now runs on the GPU. However, before integration, unique norms of |G| are identified, and that sill runs on the CPU. For large systems, this step now dominates.

This PR ports the unique |G| identification to the GPU by changing the logic. It now sorts the vector of |G|, and uses a combination of `diff` and `cumsum` to identify and index unique |G| values. These are all GPU friendly functions, where as the current solution of using a dictionary with |G| as key is not. This PR also centralizes the logic, thus reducing code duplication.

In terms of timings, the impact is substential. For a 216 atoms rattled aluminium cell, we have:

For master:
```
compute_stresses_cart                      1    56.0s   65.0%   56.0s   5.57GiB   75.3%  5.57GiB
  PlaneWaveBasis                           6    35.3s   41.0%   5.88s   5.54GiB   74.9%   946MiB
    Instantiation Ewald                    6    23.0s   26.7%   3.83s    215KiB    0.0%  35.8KiB
      precomp: Ewald                       6    23.0s   26.7%   3.83s    207KiB    0.0%  34.5KiB
    Instantiation Xc                       6    5.18s    6.0%   863ms   1.37GiB   18.5%   233MiB
    Instantiation AtomicLocal              6    5.01s    5.8%   834ms   1.91GiB   25.8%   326MiB
    Instantiation AtomicNonlocal           6    1.76s    2.0%   294ms   1.52GiB   20.5%   259MiB
```

And with this PR:
```
compute_stresses_cart                      1    45.6s   61.3%   45.6s   2.88GiB   66.4%  2.88GiB
  PlaneWaveBasis                           6    25.2s   33.9%   4.19s   2.86GiB   65.8%   487MiB
    Instantiation Ewald                    6    22.9s   30.9%   3.82s    215KiB    0.0%  35.8KiB
      precomp: Ewald                       6    22.9s   30.9%   3.82s    207KiB    0.0%  34.5KiB
    Instantiation AtomicNonlocal           6    1.47s    2.0%   245ms   1.47GiB   33.9%   251MiB
    Instantiation Xc                       6    458ms    0.6%  76.3ms    168MiB    3.8%  28.1MiB
    Instantiation AtomicLocal              6    160ms    0.2%  26.7ms    485MiB   10.9%  80.8MiB
```

The impact is even greater on another benchmark system, a 4x4 MoS2 monolayer supercell with 20 Ang of vacuum:

For master:
```
compute_stresses_cart                      1    56.2s   69.0%   56.2s   14.0GiB   86.6%  14.0GiB
  PlaneWaveBasis                           6    32.6s   40.0%   5.43s   14.0GiB   86.3%  2.33GiB
    Instantiation AtomicLocal              6    13.9s   17.1%   2.32s   5.70GiB   35.2%  0.95GiB
    Instantiation Xc                       6    12.1s   14.9%   2.02s   4.04GiB   24.9%   690MiB
    Instantiation AtomicNonlocal           6    5.24s    6.4%   873ms   1.04GiB    6.4%   178MiB
    Instantiation Ewald                    6    714ms    0.9%   119ms   63.6KiB    0.0%  10.6KiB
      precomp: Ewald                       6    714ms    0.9%   119ms   55.5KiB    0.0%  9.24KiB
```

And this PR:
```
compute_stresses_cart                      1    28.0s   58.0%   28.0s   5.45GiB   80.5%  5.45GiB
 PlaneWaveBasis                           6    5.19s   10.7%   865ms   5.41GiB   80.0%   924MiB
    Instantiation AtomicNonlocal           6    1.94s    4.0%   324ms    292MiB    4.2%  48.6MiB
    Instantiation Xc                       6    1.48s    3.1%   246ms    491MiB    7.1%  81.8MiB
    Instantiation Ewald                    6    712ms    1.5%   119ms   63.6KiB    0.0%  10.6KiB
      precomp: Ewald                       6    712ms    1.5%   119ms   55.5KiB    0.0%  9.24KiB
    Instantiation AtomicLocal              6    424ms    0.9%  70.6ms   1.43GiB   21.1%   244MiB
```

Note that forces are also positively impacted, since form factors are also computed there. I've run various tests on the CPU too, and there is no regression in timings.

Finally, with the combinations of #1388, #1389 and this PR, stress calculations of large systems go from overly expensive to perfectly acceptable:

| System | master total time (s)| master stress time (s) | all 3 PRs total time (s) | all 3 PRs stress time (S) |
|----------|----------|----------|----------|----------|
|    216 rattled aluminium      |    86.7      |    56.0      |    32.7      |    6.5      |
|     4x4 MoS2 supercell    |     88.8     |     56.2     |      36.9    |     10.7     |

Note that force acceleration also contributes to the total calculation going down.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a94a1407fa6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
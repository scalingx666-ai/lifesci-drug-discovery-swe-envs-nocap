# Issue

**Title:** Fix profiling and type stability of DftHamiltonian multiplication

## Description

Two fixes:
1. Properly record the `local` timer output. In my runs it was simply missing, which I attribute to `threadid()` being generally unreliable. Additionally, we now only allocate one `TimerOutput` per thread rather than per band.
2. Fix type instability **inside the hot per-band loop** by adding type parameters to `DftHamiltonianBlock`.

With extra profiling sections, before the 2nd commit:
```
    DftHamiltonian multiplication      839    42.4s   62.3%  50.5ms   1.28GiB   20.5%  1.56MiB
      parallel for                     839    38.4s   56.4%  45.7ms    563MiB    8.8%   687KiB
        local                        9.39k    25.9s   38.0%  2.76ms    259MiB    4.1%  28.2KiB
      nonlocal                         839    3.15s    4.6%  3.76ms    124MiB    1.9%   151KiB
      normalized potential             839    679ms    1.0%   809μs    618MiB    9.7%   754KiB
      kinetic                          839    149ms    0.2%   177μs   3.64MiB    0.1%  4.45KiB
      allocate storages                839   14.6ms    0.0%  17.5μs    675KiB    0.0%     824B
```
Notice all the lost time between `parallel for` and `local` in the first. Additionally, `local` is allocating a lot even though it shouldn't (because of dynamic dispatch).

After the 2nd commit:
```
    DftHamiltonian multiplication      849    27.3s   53.6%  32.2ms    690MiB   12.8%   832KiB
      parallel for                     849    23.8s   46.7%  28.0ms   4.73MiB    0.1%  5.71KiB
        local                        9.43k    23.2s   45.6%  2.46ms   2.16MiB    0.0%     240B
      nonlocal                         849    3.17s    6.2%  3.73ms   62.3MiB    1.2%  75.2KiB
      normalized potential             849    228ms    0.4%   268μs    622MiB   11.6%   750KiB
      kinetic                          849    139ms    0.3%   164μs    328KiB    0.0%     396B
      allocate storages                849   1.85ms    0.0%  2.18μs    332KiB    0.0%     400B
```
Almost all the time of `parallel for` is in `local` and the allocations got drastically reduced. Overall a ~1.5x speedup in this case! On the GPU this could also make a large difference @abussy.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d0b8ec964bce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
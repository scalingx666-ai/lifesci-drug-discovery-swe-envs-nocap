# Issue

**Title:** refactor(Atom): do not allocate map without atom properties

## Description

This makes the per-atom property map an optional field. Some (most?) formats don't make use of per-atom properties. Allocating the map for every atom nonetheless comes with quite some overhead. This is noticeable for frames with many atoms especially.

When reading 'ubiquitin.xtc' a ~11% speedup is observable (cf. [comparison to other implementations](https://github.com/chemfiles/benchmarks)).
For a `.nc` file with 50k atoms the speedup is ~19% for reading and ~7% for writing.

Ideally, this can be superseded by a more data-oriented approach as in #288.

This changes the user-facing API.


<details>
<summary>Benchmarking</summary>
R/W 1k steps with 50k atoms as `.nc` from C++ in a `tmpfs` ramdisk.

# master
```
Benchmark 1: ./bench_write
  Time (mean ± σ):     11.704 s ±  0.325 s    [User: 8.692 s, System: 3.004 s]
  Range (min … max):   10.672 s … 12.207 s    25 runs
 
Benchmark 1: ./bench_read
  Time (mean ± σ):      1.725 s ±  0.015 s    [User: 1.674 s, System: 0.050 s]
  Range (min … max):    1.697 s …  1.759 s    25 runs
```
# PR
```
Benchmark 1: ./bench_write
  Time (mean ± σ):     10.854 s ±  0.369 s    [User: 7.638 s, System: 3.209 s]
  Range (min … max):   10.102 s … 11.920 s    25 runs
 
Benchmark 1: ./bench_read
  Time (mean ± σ):      1.390 s ±  0.014 s    [User: 1.335 s, System: 0.054 s]
  Range (min … max):    1.370 s …  1.428 s    25 runs
```
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa2e68d57893`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
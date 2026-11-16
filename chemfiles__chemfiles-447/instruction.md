# Issue

**Title:** refactor(BinaryFile): swap and write binary data in buffered chunks

## Description

I'm currently in the process of rewriting the XTC and TRR parser based on the new `BinaryFile`.
While doing so, I couldn't reach the _writing_ speed obtained with `xdrfile`.
These formats frequently write large chunks of data (e.g. the position array) at once.
Before this PR, this involved a lot of overhead for swapping and writing individual values.
By using a buffer for swapping and writing, these chunks can be written at once without that much overhead.

For XTC/TRR it's also helpful to skip larger chunks of data without parsing it and to get the file size.
This PR introduces two functions for that in `BinaryFile`.

Besides this, there are also some misc changes:

 - Some minor adaptations in the CML parser and `span`.
 - Use the new skip function to skip the padding in NetCDF files.
 - Fix the exception strings for reading a `BinaryFile`.
 It seems that `fread` does not make use of `errno` (at least on my Linux machine) when reading beyond EOF.
 This results in error messages ending in 'Success' which in a bit confusing.

Some preliminary benchmarks show that the NetCDF R/W performance does not deteriorate.
Unfortunately, the NetCDF parser based on `mmap` does not really benefit from this PR because mostly single values are written. (Might be interesting to see if an buffered file stream would be beneficial.)
Interestingly, the `cstdio` version closes the gap to the `mmap` version.

<details>
<summary>Benchmarking</summary>
R/W 1k steps with 50k atoms as `.nc` from C++ in a `tmpfs` ramdisk.

# mmap
## write
### master
```
  Time (mean ± σ):     11.590 s ±  0.414 s    [User: 8.584 s, System: 2.999 s]
  Range (min … max):   10.661 s … 12.093 s    25 runs
```
### PR
```
  Time (mean ± σ):     11.033 s ±  0.374 s    [User: 8.182 s, System: 2.844 s]
  Range (min … max):   10.223 s … 11.580 s    25 runs
```
## read
### master
```
  Time (mean ± σ):      1.750 s ±  0.030 s    [User: 1.703 s, System: 0.046 s]
  Range (min … max):    1.702 s …  1.806 s    25 runs
```
### PR
```
  Time (mean ± σ):      1.749 s ±  0.032 s    [User: 1.701 s, System: 0.048 s]
  Range (min … max):    1.705 s …  1.808 s    25 runs
```
# cstdio
## write
### master
```
  Time (mean ± σ):     12.803 s ±  0.321 s    [User: 9.673 s, System: 3.121 s]
  Range (min … max):   11.911 s … 13.302 s    25 runs
```
### PR
```
  Time (mean ± σ):     11.140 s ±  0.325 s    [User: 8.102 s, System: 3.032 s]
  Range (min … max):   10.083 s … 11.614 s    25 runs
```
## read
### master
```
  Time (mean ± σ):      1.745 s ±  0.025 s    [User: 1.625 s, System: 0.119 s]
  Range (min … max):    1.690 s …  1.829 s    25 runs
```
### PR
```
  Time (mean ± σ):      1.731 s ±  0.026 s    [User: 1.608 s, System: 0.122 s]
  Range (min … max):    1.698 s …  1.810 s    25 runs
```
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `17a14fca75cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
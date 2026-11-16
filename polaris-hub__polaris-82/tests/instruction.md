# Issue

**Title:** feat: consolidating metadata for opening zarr files in read mode

## Description

## Changelogs

Incorporated Zarr function that [consolidates metadata](https://zarr.readthedocs.io/en/stable/tutorial.html#consolidating-metadata) when opening a Zarr group in read mode. This results in reduced number of `ls` calls and increases the speed in reading from the Zarr group.


#### Profiling without consolidation
```Profiling Report
====================================================================================================
Date: 2024-03-28
Time: 16:21:26
Size: 8.0 KB
Repeats: 1
Polaris version: 0.0.2.dev191+g82e7db2
Zarr version: 2.17.1
====================================================================================================
                         Creating the Zarr archive: 0:00:00.002254 ± 0:00:00
         Creating dataset from Source Zarr archive: 0:00:00.003214 ± 0:00:00
                      Uploading dataset to the Hub: 0:00:27.666530 ± 0:00:00
                          Loading dataset from Hub: 0:00:01.549233 ± 0:00:00
                   Iterating over dataset (remote): 0:00:25.385904 ± 0:00:00
                          Caching dataset to local: 0:00:18.538832 ± 0:00:00
                    Iterating over dataset (local): 0:00:00.001493 ± 0:00:00
           Baseline Zarr only upload to Cloudflare: 0:00:00.636373 ± 0:00:00
             Baseline dataset upload to Cloudflare: 0:00:03.207451 ± 0:00:00
       Baseline Zarr only download from Cloudflare: 0:00:00.251135 ± 0:00:00
         Baseline dataset download from Cloudflare: 0:00:00.432873 ± 0:00:00
====================================================================================================
                        Actual / Baseline - Upload: 8.626 ± 0.000
                      Actual / Baseline - Download: 42.827 ± 0.000  
```
#### Profiling with consolidation
```
Profiling Report
====================================================================================================
Date: 2024-04-04
Time: 11:15:12
Size: 8.0 KB
Repeats: 2
Polaris version: dev
Zarr version: 2.16.1
====================================================================================================
                         Creating the Zarr archive: 0:00:00.018600 ± 0:00:00.007932
         Creating dataset from Source Zarr archive: 0:00:00.021886 ± 0:00:00.002237
                      Uploading dataset to the Hub: 0:00:35.845067 ± 0:00:02.073791
                          Loading dataset from Hub: 0:00:01.928347 ± 0:00:00.003685
                          Caching dataset to local: 0:00:03.662794 ± 0:00:00.299349
                    Iterating over dataset (local): 0:00:00.005156 ± 0:00:00.000391
           Baseline Zarr only upload to Cloudflare: 0:00:00.973820 ± 0:00:00.110363
             Baseline dataset upload to Cloudflare: 0:00:03.534744 ± 0:00:00.056176
       Baseline Zarr only download from Cloudflare: 0:00:00.447640 ± 0:00:00.131711
         Baseline dataset download from Cloudflare: 0:00:00.386626 ± 0:00:00.024372
====================================================================================================
                        Actual / Baseline - Upload: 10.134 ± 0.426
                      Actual / Baseline - Download: 9.463 ± 0.178

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb499482d310`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
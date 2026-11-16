# Issue

**Title:** feat: Listings Caching implementation using fsspec dircache

## Description

## Changelogs

Implementing a listings caching system using fsspec's dircache to reduce the number of `ls` calls made during zarr upload/download. 

The fsspec `info()` method was the method that was resulting in all of the `ls` calls being made during upload so I tried targeting this method by using a listings caching. Given that listings caching is activated, each call to `ls` checks the path for cached listings and if none are found, it will check the listings for the parent path. This was an idea to solve the problem of checking child paths even though we learn that the parent path is empty:

```ls_path:  /storage/dataset/lmtroper/93a16e4534324def975d5a97285722c5/ls/
[]
ls_path:  /storage/dataset/lmtroper/93a16e4534324def975d5a97285722c5/ls/data.zarr
[]
ls_path:  /storage/dataset/lmtroper/93a16e4534324def975d5a97285722c5/ls/data.zarr/.zgroup
[]
pipe_path:  /storage/dataset/lmtroper/93a16e4534324def975d5a97285722c5/data.zarr/.zgroup
ls_path:  /storage/dataset/lmtroper/93a16e4534324def975d5a97285722c5/ls/data.zarr
[{'name': 'dataset/lmtroper/93a16e4534324def975d5a97285722c5/data.zarr/.zgroup', 'size': 24, 'type': 'file'}]
```

Profiling with listing caching:
```
Profiling Report
====================================================================================================
Date: 2024-04-09
Time: 15:12:45
Size: 953.67 MB
Repeats: 1
Polaris version: dev
Zarr version: 2.16.1
====================================================================================================
                         Creating the Zarr archive: 0:00:01.336539 ± 0:00:00
         Creating dataset from Source Zarr archive: 0:00:01.979446 ± 0:00:00
                      Uploading dataset to the Hub: 0:14:26.429550 ± 0:00:00
                          Loading dataset from Hub: 0:00:03.912605 ± 0:00:00
                          Caching dataset to local: 0:23:45.847385 ± 0:00:00
           Baseline Zarr only upload to Cloudflare: 0:04:38.541630 ± 0:00:00
             Baseline dataset upload to Cloudflare: 0:05:00.708451 ± 0:00:00
       Baseline Zarr only download from Cloudflare: 0:01:16.668102 ± 0:00:00
         Baseline dataset download from Cloudflare: 0:01:12.491876 ± 0:00:00
====================================================================================================
                        Actual / Baseline - Upload: 2.881 ± 0.000
                      Actual / Baseline - Download: 19.669 ± 0.000

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `69751c3c36a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
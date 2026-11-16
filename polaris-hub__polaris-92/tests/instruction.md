# Issue

**Title:** feat: Copy a Zarr archive to the Hub using copy_store for increased efficient

## Description

## Changelogs

Replaced `copy_all` with `copy_store` when copying a Zarr archive to the Hub. The changes should increase efficiency as `copy_store` does not de-compress and re-compress the data during copying ([see documentation here](https://zarr.readthedocs.io/en/stable/api/convenience.html#zarr.convenience.copy_store)).

Below is the impact it had on profiling:

With `copy_all`:
```Profiling Report
====================================================================================================
Date: 2024-04-04
Time: 17:29:52
Size: 953.67 MB
Repeats: 5
Polaris version: 0.0.2.dev191+g82e7db2
Zarr version: 2.17.1
====================================================================================================
                         Creating the Zarr archive: 0:00:01.344764 ± 0:00:00.151870
         Creating dataset from Source Zarr archive: 0:00:01.509610 ± 0:00:00.201476
                      Uploading dataset to the Hub: 0:08:58.749664 ± 0:00:24.787134
                          Loading dataset from Hub: 0:00:02.294858 ± 0:00:00.129297
                          Caching dataset to local: 0:10:36.877163 ± 0:00:35.494129
                    Iterating over dataset (local): 2:05:54.817060 ± 0:02:11.140053
           Baseline Zarr only upload to Cloudflare: 0:00:30.342002 ± 0:00:01.761582
             Baseline dataset upload to Cloudflare: 0:00:34.035674 ± 0:00:00.615563
       Baseline Zarr only download from Cloudflare: 0:00:44.472856 ± 0:00:21.117384
         Baseline dataset download from Cloudflare: 0:00:33.714192 ± 0:00:01.377525
====================================================================================================
                        Actual / Baseline - Upload: 15.843 ± 0.939
                      Actual / Baseline - Download: 18.926 ± 1.369
```

With `copy_store`:

```Profiling Report
====================================================================================================
Date: 2024-04-09
Time: 06:45:36
Size: 953.67 MB
Repeats: 1
Polaris version: dev
Zarr version: 2.16.1
====================================================================================================
                         Creating the Zarr archive: 0:00:01.407685 ± 0:00:00
         Creating dataset from Source Zarr archive: 0:00:01.874611 ± 0:00:00
                      Uploading dataset to the Hub: 0:28:05.252655 ± 0:00:00
                          Loading dataset from Hub: 0:00:03.237522 ± 0:00:00
                          Caching dataset to local: 0:16:53.128378 ± 0:00:00
           Baseline Zarr only upload to Cloudflare: 0:04:31.668470 ± 0:00:00
             Baseline dataset upload to Cloudflare: 0:04:43.972480 ± 0:00:00
       Baseline Zarr only download from Cloudflare: 0:01:09.703651 ± 0:00:00
         Baseline dataset download from Cloudflare: 0:01:11.038993 ± 0:00:00
====================================================================================================
                        Actual / Baseline - Upload: 5.935 ± 0.000
                      Actual / Baseline - Download: 14.262 ± 0.000
```


**Note:** We did not implement `copy_store` for downloading datasets (only uploading) as it resulted in an increase in caching the dataset locally. See below:

`copy_store` for both upload and download:

```Profiling Report
====================================================================================================
Date: 2024-04-09
Time: 14:02:09
Size: 95.37 MB
Repeats: 1
Polaris version: dev
Zarr version: 2.16.1
====================================================================================================
                         Creating the Zarr archive: 0:00:00.223971 ± 0:00:00
         Creating dataset from Source Zarr archive: 0:00:00.242384 ± 0:00:00
                      Uploading dataset to the Hub: 0:07:06.433739 ± 0:00:00
                          Loading dataset from Hub: 0:00:02.718317 ± 0:00:00
                          Caching dataset to local: 0:04:54.390313 ± 0:00:00
           Baseline Zarr only upload to Cloudflare: 0:00:32.339057 ± 0:00:00
             Baseline dataset upload to Cloudflare: 0:00:33.148623 ± 0:00:00
       Baseline Zarr only download from Cloudflare: 0:00:09.478066 ± 0:00:00
         Baseline dataset download from Cloudflare: 0:00:07.696965 ± 0:00:00
====================================================================================================
                        Actual / Baseline - Upload: 12.864 ± 0.000
                      Actual / Baseline - Download: 38.248 ± 0.000
```
                      
                      
                      
`copy_store` for just upload:


```Profiling Report
====================================================================================================
Date: 2024-04-09
Time: 14:16:02
Size: 95.37 MB
Repeats: 1
Polaris version: dev
Zarr version: 2.16.1
====================================================================================================
                         Creating the Zarr archive: 0:00:00.188619 ± 0:00:00
         Creating dataset from Source Zarr archive: 0:00:00.235259 ± 0:00:00
                      Uploading dataset to the Hub: 0:06:52.969075 ± 0:00:00
                          Loading dataset from Hub: 0:00:02.182547 ± 0:00:00
                          Caching dataset to local: 0:04:19.006523 ± 0:00:00
           Baseline Zarr only upload to Cloudflare: 0:00:32.249822 ± 0:00:00
             Baseline dataset upload to Cloudflare: 0:00:33.095662 ± 0:00:00
       Baseline Zarr only download from Cloudflare: 0:00:07.731580 ± 0:00:00
         Baseline dataset download from Cloudflare: 0:00:07.948864 ± 0:00:00
====================================================================================================
                        Actual / Baseline - Upload: 12.478 ± 0.000
                      Actual / Baseline - Download: 32.584 ± 0.000

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1008662a73c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
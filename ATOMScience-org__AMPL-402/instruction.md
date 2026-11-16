# Issue

**Title:** create a mchip_dev_requirements to fix the issue with 'matplotcheck' …

## Description

…install issue on arm chip

The [error](https://github.com/ATOMScience-org/AMPL/actions/runs/15145088743/job/42584289530) was:

```
#11 41.40 Collecting rasterio (from matplotcheck->-r ./pip/dev_requirements.txt (line 12))
#11 41.42   Downloading rasterio-1.4.3.tar.gz (442 kB)
...
#11 86.49   error: subprocess-exited-with-error
#11 86.49   
#11 86.49   × Getting requirements to build wheel did not run successfully.
#11 86.49   │ exit code: 1
#11 86.49   ╰─> [2 lines of output]
#11 86.49       WARNING:root:Failed to get options via gdal-config: [Errno 2] No such file or directory: 'gdal-config'
#11 86.49       ERROR: A GDAL API version must be specified. Provide a path to gdal-config using a GDAL_CONFIG environment variable or use a GDAL_VERSION environment variable.
...
#11 87.31 note: This error originates from a subprocess, and is likely not a problem with pip.
#11 ERROR: process "/dev/.buildkit_qemu_emulator /bin/sh -c pip install -U pip &&     pip install --no-cache-dir     --trusted-host pypi.python.org     --trusted-host files.pythonhosted.org     --trusted-host pypi.org     --trusted-host data.dgl.ai     --trusted-host download.pytorch.org     -r ./pip/dev_requirements.txt" did not complete successfully: exit code: 1
```

- It was due to `matplotcheck` package from `dev_requirements.txt`. Since it's used to run plotting tests, not required for the docker image, created a dev_requirements.txt for mchip.
- Ran the test manually and it went fine. 

```
 export PLATFORM=arm
 export ENV=prod
 export ARCH="linux/arm64"
 make build-docker
```
Will test the image on mchip environment and push to the docker repo.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b89515e8339c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
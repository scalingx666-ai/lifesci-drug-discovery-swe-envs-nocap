# Issue

**Title:** Add Docker image

## Description

## Docker Image

This PR includes the logic to run PLAPT in a Docker container, which has the Python and CUDA dependencies pre-installed.

1. Build the Docker image locally:

   ```bash
   docker build -t plapt .
   ```

   Or pull the pre-built image from Docker Hub:

   ```bash
   docker pull cford38/plapt:latest
   ```

2. Run the Docker container:

   ```bash
   docker run --gpus all --rm --name plapt -it plapt /bin/bash
   # docker run --gpus all --rm --name plapt -it cford38/plapt:latest /bin/bash
   ```
> [!NOTE]
> This image does not include all of the model weights, which will be downloaded the first time you run PLAPT inside in the container.


---------
In a future update, we could pre-download the model weights and include them in the container.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e20b4009d979`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
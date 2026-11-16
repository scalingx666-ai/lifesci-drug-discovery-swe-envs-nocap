# Issue

**Title:** Update Dockerfile to run the bio-diffusion model(s)

## Description

This PR includes an updated Dockerfile that contains the conda environment and other system dependencies for running the `bio-diffusion` models.

## Usage

To run this project in a Docker container, you can use the following commands:

```bash
## Build the image
docker build -t bio-diffusion .

## Run the container (with GPUs and mounting the current directory)
docker run -it --gpus all -v .:/mnt --name bio-diffusion bio-diffusion
```
__Note:__ You will still need to download the checkpoints and data as described in the installation guide. Then, update the Python commands to point to the desired local location of your files (e.g., `/mnt/checkpoints` and `/mnt/outputs`) once in the container.


## Other Info:

- The Dockerfile uses the `pytorch/pytorch:1.12.1-cuda11.3-cudnn8-runtime` base image
- The `environment.yaml` file has been updated to comment out a few dependencies that were causing problems. The Python scripts still seem to run, but full tests should be done to verify. Alternatively, these dependencies could be updated to be less specific, which may solve some of the "environment solving" issues.
  - Example:  `yaml=0.2.5=h7f98852_2` --> `yaml=0.2.5`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `51021a5ff582`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add Docker Image

## Description

This PR includes a `Dockerfile`, a simplified conda `.yaml` file, and an updated `README.md` that describes how to run FlowDock from inside the container.

I have pushed the Docker image to Docker Hub: https://hub.docker.com/repository/docker/cford38/flowdock

### Notes:

- We need to further simplify the `environments/flowdock_environment_docker.yaml` file to generalize the versions needed of each library. This current conda environment took hours to solve, likely due to the overly specific versions described in the .yaml file.
- This has been tested on the inferencing functionality (`python flowdock/sample.py ...`) and inferences well with CUDA acceleration. However, it has not been tested on the training or evaluation FlowDock tasks.
- This Docker image does not contain the checkpoints as it is already quite large (>12GB). Thus, users will need to download the desired checkpoint locally and run the Docker image with the local checkpoint directory mounted as a volume.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `86c593fb8113`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
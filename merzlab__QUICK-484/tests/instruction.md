# Issue

**Title:** Added compatibility for alternative gpu architectures for build-test cuda

## Description

Added compatibility for the following architectures (on top of ampere) to reduce queuing time and improve availability: volta, turing, adalovelace

Works for both enablef=TRUE and enbalef=FALSE.

Also correct name of jobs to include cmake.

List of GPUs on NRP Nautilus that can be requested:
- NVIDIA-A10
- NVIDIA-GeForce-RTX-3090
- NVIDIA-GeForce-RTX-2080-Ti
- NVIDIA-RTX-A4000
- NVIDIA-RTX-A5000
- NVIDIA-L4
- NVIDIA-L40
- NVIDIA-L40S
- Tesla-V100-SXM2-32GB
- Tesla-V100-SXM2-16GB

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b07e34361833`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
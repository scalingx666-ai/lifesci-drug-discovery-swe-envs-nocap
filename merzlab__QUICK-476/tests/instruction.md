# Issue

**Title:** MVP CI/CD Implementation for QUICK CUDA (without f functions) Build and Test Workflow

## Description

Ensures that on every push and pull request, automate tests on a runner on NRP Nautilus.

Cannot build with f functions yet since the runner fails during build. Working on reconfiguring the QUICK runner to be able to handle building with f functions. Will introduce as a separate workflow.

Currently can only build/test on NVIDIA-A10s. Will introduce compatibility for other architectures next to ensure more availability.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5446219cf8b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
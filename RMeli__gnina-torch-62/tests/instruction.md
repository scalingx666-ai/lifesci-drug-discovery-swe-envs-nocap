# Issue

**Title:** Update supported Python, move to pyproject.toml, and fix CI

## Description

Additionally, loosen the threshold for the checks on pre-trained models. Results are slightly different using PyTorch 2.11 and CUDA 13.1.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b1136114448`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
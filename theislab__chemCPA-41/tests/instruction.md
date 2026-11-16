# Issue

**Title:** Calc disentanglement loss on GPU

## Description

- First working version of GPU disentanglement
- Lower the epochs for disentangle
- Add timestamp to data logging

Very roughly, running 1000 epochs to calc just the perturbation disentanglement took ~20 minutes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0febe35d7c3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
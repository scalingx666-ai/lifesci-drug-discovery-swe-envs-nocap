# Issue

**Title:** Fix device mismatches

## Description

This PR fixes some remaining device mismatches to allow running the program on CUDA devices.

NOTE: We use `torch.scatter_reduce`, which has no CUDA support in PyTorch 1.11 and only runs on CPU ([see comments](https://github.com/grimme-lab/xtbML/blob/8716dc06ceb5ebc4a3a010b90abb9d539f1c2405/src/dxtb/basis/indexhelper.py#L210) and #57). Consequently, we definitely need to upgrade to PyTorch 1.12 for _dxtb_  to run on GPUs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b96d40b708a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
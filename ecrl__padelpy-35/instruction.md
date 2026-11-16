# Issue

**Title:** Add option to control running time per molecule

## Description

The current implementation does not support controlling the maximum time for each molecule. But there are some cases that `PaDEL` is not capable of computing descriptors because of force field restrictions. In order to overcome these issues, adding a flag to control the running time for each molecule seems a good choice. Thanks for reviewing the codes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `901772d429d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
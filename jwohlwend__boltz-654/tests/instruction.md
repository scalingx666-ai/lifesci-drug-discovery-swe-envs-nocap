# Issue

**Title:** Allocate tensors directly on target device

## Description

I was hitting a weird crash when running Boltz1 with DDP on ROCm that I narrowed down to one of these. Allocating directly on device seems to fix it, and is also cleaner and a minor performance optimization, so I went through and updated several other places as well (obviously may have missed some).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb04aeccdd48`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
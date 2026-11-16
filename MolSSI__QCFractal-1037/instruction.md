# Issue

**Title:** Allow separate QCEngine and worker memory limits

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
 Adds an optional qcengine_memory_per_worker setting so QCEngine can receive less memory than
 the worker allocation. This leaves memory for process and system overhead, reducing the risk
 of workers being killed for exceeding their allocation.

 When unset, it defaults to memory_per_worker, preserving existing behavior.
## Status
- [ ] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `23be93d4f54f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
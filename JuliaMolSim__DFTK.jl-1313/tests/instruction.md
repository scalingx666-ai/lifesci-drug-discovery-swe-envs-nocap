# Issue

**Title:** Safe GPU-aware MPI communication

## Description

Before MPI communication of GPU buffers, the device must be synchronized. If not, there is a real risk of race condition because CPU and GPU run asynchronously. This has no effect on CPU performance. On the GPU, this cannot be avoided.

For reference, here is a  updating the relevant documentation in MPI.jl. The problem has been known for a while, but never properly documented. The PR also links to a slack thread where the problem is discussed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b6b1f7d2a9c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
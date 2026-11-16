# Issue

**Title:** Build chemfiles on ARMv7 / AARCH64

## Description

A few minor changes required to build and run chemfiles om ARM platforms.

I did not test on real hardware since I don't have any (anyone with a raspberry pi around?), but the code cross-compile (using https://gist.github.com/Luthaf/46c711a2f205ab99d81116848cd45ad3) and run with qemu, so this is a good first step.

I also got chemfiles to compile on PowerPC64 targets. There seems to be an endianness issue with the molfile DCD reader on ppc64le, and a lot a tests error with ppc64, so this will have to wait.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `efacbf09230e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
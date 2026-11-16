# Issue

**Title:** Limit memory used by BinaryFile to 100MiB in mmap mode

## Description

We now load/unload 100MiB chunks, making sure loading large files don't fill up memory and leave some for processing of the data.

xref

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b01e4f9839f2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
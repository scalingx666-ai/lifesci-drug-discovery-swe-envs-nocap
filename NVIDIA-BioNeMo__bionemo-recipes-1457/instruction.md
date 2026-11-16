# Issue

**Title:** Enable pre-fetching for ContextParallelDataLoaderWrapper

## Description

Adds a prefetch thread to `ContextParallelDataLoaderWrapper` that fetches the next batch asynchronously, allowing us to overlap some of the communication for CP dataloader with the forward/backward pass 

Includes changes from #1415

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `277a8096dfc8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
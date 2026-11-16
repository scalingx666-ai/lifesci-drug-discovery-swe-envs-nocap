# Issue

**Title:** Speedup package import time

## Description

We've been looking at the import time of the mlptrain package, which takes over a second on the cluster, and around 620ms on my dev machine with NVMe drive. Importing `autode` by itself takes 465 ms on main branch.

One of the easy wins is to import `matplotlib` only when needed, which saves around 160 ms.

Other potential improvements would come from delayed import of scipy and / or RDkit. But those would require more changes --- happy to open a separate PR if that is desired.

Corresponding PR on `mlptrain` repo:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05b2d985b5f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
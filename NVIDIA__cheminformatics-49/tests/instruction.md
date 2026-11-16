# Issue

**Title:** Rilango/bug n cluster

## Description

Changing the 'number of cluster' and reclustering did not pass the new value of
'number of cluster'. This patch unblocks the event to pass the new value to
workflow class.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83889de7c423`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
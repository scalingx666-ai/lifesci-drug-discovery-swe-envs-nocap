# Issue

**Title:** fix pod deletion on job deletion

## Description

I noticed that pods (which are started by jobs) weren't being cleaned up.  I set a propagation policy of "background" so when the job is deleted, the pods will be deleted asynchronously (it's possible to do foreground, but I figured that would just slow down the redun k8s executor unnecessarily).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `208d4c54afce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** gdma: remove git subprocess logic to obtain commit and hardcode it

## Description

. For some reasons beyond my understanding, `fetchgit` with `leaveDotGit = true` gives a different hash each time. Thus, I'm removing the original reason to keep the `.git`; obtaining the commit by calling into git. Instead I'm just hardcoding the commit string now.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0386c15f4b2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** gmda: fix hash, update commit

## Description

The GDMA hash broke somehow ... I don't know how, I suspect it has something to do with `leaveDotGit = true` but as the commit didn't change I'm somewhat lost. I've updated to the most recent commit anyway.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8273d036e59`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
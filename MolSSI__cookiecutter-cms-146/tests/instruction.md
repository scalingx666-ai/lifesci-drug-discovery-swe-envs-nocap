# Issue

**Title:** Update for NEP

## Description

Drop python 3.7 from testing matrxi and add python 3.10, using quotes to avoid [yaml parsing issues](https://dev.to/hugovk/the-python-3-1-problem-85g)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `918de2aa4222`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
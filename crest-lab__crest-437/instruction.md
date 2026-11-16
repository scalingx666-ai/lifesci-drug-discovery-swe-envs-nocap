# Issue

**Title:** g-xTB with numerical gradients

## Description

This adds g-xTB subprocesses with numerical gradients.
Note, this will be too expensive for sampling applications, but simple runtypes like a standalone geometry optimization will work fine.
For better distinction the flag `--gxtb_dev` is used rather than `--gxtb`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `148b2b1e215a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
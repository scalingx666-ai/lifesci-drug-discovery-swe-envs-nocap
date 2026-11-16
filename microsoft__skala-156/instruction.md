# Issue

**Title:** Fix GPU tests on main + add trigger for GPU tests

## Description

Fix missing `libcusolver` in GPU tests and ensure that GPU tests are triggered on PRs (only if they come from this repo) if they touch GPU-dependent code so we don't have surprising failures on main

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e58ec2d6b0ed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Expand upon dataset matching tests

## Description

Add more comprehensive dataset matching test which downloads the dataset and checks for equality. Also added instructions to the README on how to run the test. This should allow people to verify whether dockstring matches the dataset on their system.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc7997c33cb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Increase timeout for Windows_VS2022_x64_dll CI job

## Description

The win64_dll CI job has been timing out a lot lately. For some reason it's set to only have 120min while the other win64 job has 150... this fixes that.

We're going to disable these anyway in the not-too-distant future, but it's irritating to have things keep failing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a3f2eed91866`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Exclude packages that are newer than 7 days for installation

## Description

This PR improves the configuration of BayBE such that only package version older than 7 days can be installed.

I have tested this locally and can confirm that it works: I've attempted to raise the version of `uv` itself in this PR, which was not possible as the latest version of `uv` is only 4 days old. I've also done a check using a value of 100 days, which results in an error that the necessary version `0.14.11.` of `ruff` cannot be installed. Since 100 days ago was December 20, 2025, this also checks out:
<img width="493" height="182" alt="image" src="https://github.com/user-attachments/assets/65f47630-711b-4bce-838b-0415f3a95be8" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `addf70c63f20`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
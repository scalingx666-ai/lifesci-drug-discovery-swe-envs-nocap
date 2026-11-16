# Issue

**Title:** Pin ddX version 1.0.2

## Description

Pin the ddX version to 1.0.2 to overwrite the tblite default. This includes the fix in ddsolvation/ddX#188

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33fe381adde7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
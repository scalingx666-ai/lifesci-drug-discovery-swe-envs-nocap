# Issue

**Title:** libpng removed from Ubuntu mirrors

## Description

Recently, libpng fails to install because the package cannot be found. I'm not sure why, it could have something to do with this vulnerability found on Feb 12th. https://ubuntu.com/security/notices/USN-8039-1. We need to add apt-get update to update mirrors. This solution was suggested by CoPilot and I'm not sure if I understand any long term repercussions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a37af476e2c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
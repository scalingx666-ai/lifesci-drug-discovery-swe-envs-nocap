# Issue

**Title:** Find packages, using Manifest.in, and a small fix in setup.py

## Description

As discussed in issue #78, this PR adds:

- package autodiscovery 
- data management through MANIFEST.in

Also, while looking at setup.py, I found that `author_email` was mentioned again in the bottom comments, but it had been already defined some lines above.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb141689e6b9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
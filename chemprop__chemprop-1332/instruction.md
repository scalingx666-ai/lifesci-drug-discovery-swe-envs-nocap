# Issue

**Title:** add v2.2.2 requirements

## Description

To make this, I pulled and ran the 2.2.2 docker image and then ran `python -m pip list --format=freeze`

Two questions:
1. This requirements list is much longer than it was for 2.2.1. Is that indicative of a mistake on my end, or did adding new requirements for v2.2.2 affect it this much?
2. Is there a more automatic way of doing this when we release new versions? Or we could add this step to our developer docs in the section about making a release.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b75ace5d4e86`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
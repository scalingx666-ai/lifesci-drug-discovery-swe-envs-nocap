# Issue

**Title:** Update extras.py

## Description

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Fix a literal one-in-a-million random bug causing Psi4 to [crash](https://dev.azure.com/psi4/psi4/_build/results?buildId=6488&view=logs&j=f31c9f97-4411-58e7-49ac-fc73f645e6b6&t=140ee297-051b-5396-a86d-f0d06cd83763).
 
## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `339c81dd79de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
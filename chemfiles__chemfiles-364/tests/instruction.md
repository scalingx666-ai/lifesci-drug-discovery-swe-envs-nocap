# Issue

**Title:** Various small PDB changes

## Description

Most notably, this adds support for helix handedness & segment name; and ix the issue with duplicated residue id with different names.

Fix #330
Fix #361
Fix #362 

@frodofine I understand you no longer have much time to spend on chemfiles since you started a new job, am I right? If so I'll start asking other people for reviews =)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `76e779987394`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
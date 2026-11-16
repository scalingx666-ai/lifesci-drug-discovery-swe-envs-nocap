# Issue

**Title:** Improving the custom fingerprint creation

## Description

This PR aims to solve #64 . Now the class itself is passed to the `parallel_helper()`. 
Also it is now possible to set the name of the fingerprint from the base class init level.
Docs are updated and the new notebook about the subclassing is added.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c3f627ea392`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
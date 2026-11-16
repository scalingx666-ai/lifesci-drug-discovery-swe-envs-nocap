# Issue

**Title:** When parsing the RDKit extension for atropisomers, we should check fo…

## Description

…r conflicting information and throw an error unless we are in relaxed mode.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e51f7b45816`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
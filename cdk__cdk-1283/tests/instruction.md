# Issue

**Title:** Remove the iordf module as the JENA dependency brings in too many and…

## Description

… exposed dependencies, the CDKOWLReader/Writer should be moved to a separate project.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b0d72fa6753`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
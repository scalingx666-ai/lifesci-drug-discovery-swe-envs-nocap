# Issue

**Title:** Fix missing alpha and beta when combining xmls

## Description

## Description
This PR fixes the xml combiner CLI command to include the alpha and beta scaling when not fitting alpha and beta which was missed previously. This would cause the parameter eval tags to be incorrect and give inconsistent sigma and epsilon values compared to those calculated by qubekit directly. 


## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0df49af4b78e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
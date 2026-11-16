# Issue

**Title:** Update software citation details in CITATION.cff

## Description

Updated version, release date, title, URL, and DOI for the software citation.

It's a bit chicken and egg if the citation.cff reference the zenodo and the zenodo references the citation :-)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3609bf455605`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
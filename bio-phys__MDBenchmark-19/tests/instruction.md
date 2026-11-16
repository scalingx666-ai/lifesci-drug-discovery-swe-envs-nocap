# Issue

**Title:** Gromacs

## Description

Changes made in this Pull Request:
 - read ncores from gromacs logs
 - abstract mdengines (ground work to add other tools)


PR Checklist
------------
 - [x] CHANGELOG updated (added [news fragment](https://github.com/hawkowl/towncrier#news-fragments) into changelog directory)?
 - [x] Issue raised/referenced?
 - [x] tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d96889ef91e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
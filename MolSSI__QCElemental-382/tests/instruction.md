# Issue

**Title:** Remove old/unused cpu and dft info functionality

## Description

<!-- Thank you for your contribution! -->



## Description
<!-- Provide a brief description of the PR's purpose here. -->
QCElemental had some lookup data/info for CPU architecture and data about DFT functionals.

As far as I know, this functionality was only used 5-6 years ago in an ML project which is no longer going on. CPU info is a mismatch for this project. You could probably talk me into keeping the DFT info, but it's unlikely to ever be used. So lets remove it and see if anyone yells (willing to bet no one will miss it).

(I know a lot of it was data files, but -214k lines makes me happy)

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Remove CPU and DFT info functionality

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1c2a26d607e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
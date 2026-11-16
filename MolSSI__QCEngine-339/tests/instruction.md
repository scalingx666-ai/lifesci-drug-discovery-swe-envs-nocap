# Issue

**Title:** Make QCEngine tolerant of `cpuinfo` failure to populate `brand_raw`, `brand`

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->

Currently, we observe frequent failure of `cpuinfo` to give brand information when used within Docker containers on Pacific Research Platform. It is unclear why, but making QCEngine tolerant of this information being missing would help in production usage.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
QCEngine calls now tolerant of missing `brand_raw` or `brand` info from py-cpuinfo.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43b07131d758`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add a reader for cdxml format

## Description

added a reader for cdxml format that supports
- bond stereo information via 'notation' analog to sdfilereader
- aromaticity from bond order '1.5'

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68666d5e9861`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
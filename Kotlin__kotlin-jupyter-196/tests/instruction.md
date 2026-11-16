# Issue

**Title:** Update Lets-Plot dependencies

## Description

Update Lets-Plot dependencies: api -> 2.0.1, lib -> 2.0.2
- Artifacts published to Maven Central (was JCenter)
- JS is distributed via CDNJS (was bintray)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4cb738bd9f46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
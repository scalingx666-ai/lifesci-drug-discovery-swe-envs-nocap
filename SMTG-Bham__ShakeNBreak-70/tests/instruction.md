# Issue

**Title:** Develop

## Description

Merging to `main` so that tests are now shown as passing (was only one or two small failures due to deprecation warnings related to `doped`, rather than any issues with `ShakeNBreak` code), but won't make a new release as it's only minor tests updates

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `286bf880097b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
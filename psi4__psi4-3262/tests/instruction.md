# Issue

**Title:** Fix CI, update QCEl 0.29, QCEn 0.31, and Einsums 0.6.1

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] It's not required but check that QCElemental v0.29 (latest on c-f) works ok
- [x] Einsums v0.5 gives compile errors. v0.6.1 builds ok, though it's shortly going to be replaced by restucturing
- [x] It's not required but update to latest v0.31 QCEngine
- [x] work around a Windows GHA image bug
- [x] i-pi v3.1.1 seems to expect ASE installed, so let's not use it
- [x] the longest snowflake tests pass fine locally but take ~3m so tend to be flaky on CI. moving them to `medlong` label so won't run in ecosys

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e54962d6294`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
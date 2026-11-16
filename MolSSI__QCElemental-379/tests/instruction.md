# Issue

**Title:** avoid uncontrollable printing

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Addresses #368 as stated. I moved the printing to the error msg and allowed verbose to be passed through from Mol creation. But I wonder if your trouble was definitely around line 522 (which only printed when it was about to throw) or similar content around line 563, @jaclark5?

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e17e73addb2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
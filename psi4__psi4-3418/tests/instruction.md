# Issue

**Title:** Remove unnecessary local copy of Dimension objects from cceom/diagSS

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
PR #3356 introduced local mutable copies of the `moinfo.aoccpi`,  `moinfo.avirtpi` obejcts and their beta counterparts into cceom/diagSS
This PR provides a better solution via `const&`.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] No user-facing changes

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Replace declaring mutable dimension objects unconditionally and assigning them if needed, with `const&` in the smallest scope they are needed in. This restores the lack of copying before PR #3356.

## Checklist
- [x] No new features
- [x] CI tests are passing

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6da633d8e104`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
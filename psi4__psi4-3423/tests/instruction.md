# Issue

**Title:** Dont predicate throw in CDJK on printlevel

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
I noticed that currently the check that throws in CDJK if it is used with "wK tasked" (which is not supported in CDJK) is disarmed if the CDJK print level is zero. A sanity check like this should not be predicated on a print verbosity setting, this PR makes it unconditional.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] Some improper usages of Cholesky decomposition methods in unimplemented ways now throw an error even if the output print verbosity is set to minimal

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Check if `do_wK_ == true` in `CDJK::print_header` and throw even if `CDJK::print_ == 0`

## Checklist
- [x] No new features
- [x] Tests run by the CI are passing

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6da633d8e104`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
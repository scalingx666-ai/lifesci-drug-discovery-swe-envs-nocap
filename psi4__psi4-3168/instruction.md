# Issue

**Title:** Throw PSIEXCEPTION instead of calling abort() in detci

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Detci still has a few places where error termination is effected through printf+abort(). This PR replaces the calls to abort() in with `throw PSIEXCEPTION(msg)`.

The rest of the codebase has more of this pattern, those are subject to future PRs to keep this one small.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] A few error terminations in the detci module now print a more detailed error information to the console, instead of just the error message in the output file.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Calls to `abort()` in detci are replaced with `throw PSIEXCEPTION(msg)`, where `msg` is the relevant error message taken from the context of the `abort()`

## Checklist
- [x] No new features
- [x] Tests run by the CI are passing

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `339c81dd79de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
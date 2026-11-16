# Issue

**Title:** fix ci mamba

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] I think CI is hitting a brownout to deprecate the non-redundant mambaforge, so completing the switch. I've done it at other repos
- [x] windows nightly builds are in great demand, I don't have much more to delete to create space for them, and I'm tired of build always looking like it's failing at master.


## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b309a9aca34c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
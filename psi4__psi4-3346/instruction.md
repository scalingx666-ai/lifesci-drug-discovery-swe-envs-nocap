# Issue

**Title:** Pin the version of github-push-action used for docs, try to not force push

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Using ad-m/github-push-action@master in the action that pushes the updated docs is technically a software supply chain risk.
It handles sensitive data like a GH token, and could probably do bad things if the account of one of its maintainers was to be compromised. While the risk is remote, given how rarely it is normally updated, pinning its version would be good practice.

~~I don't see why the action was set to force push, but perhaps it would be worth seeing if we can do away with that.~~

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Pin ad-m/github-push-action to the recent 1.0 release

## Checklist
- [x] No new features

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d44eaf840fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
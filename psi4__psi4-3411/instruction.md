# Issue

**Title:** fix pytest markers and docs strictness in CI

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] with the release of QCEngine v0.50, pytest has new markers to complain about, so let's fix them pronto since all the CI is failing. borrowed from 
- [x] some of the QCSchema v2 update have broken intersphinx links in docs, which causes docs build to fail w/strict so turn that off temporarily. this is also fixed properly by 3341
- [x] we're having trouble getting PRs to 1.10.x to run, so editing the azure control file here on master, too, in case that helps.

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `336f6291401a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
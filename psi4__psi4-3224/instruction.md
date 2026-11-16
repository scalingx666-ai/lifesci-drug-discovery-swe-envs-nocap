# Issue

**Title:** fix CI

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] Einsums v0.6 needs gcc 11 or clang 16. don't want to bump psi4 requirements for opt'l dep, so bump gcc from 10->11 and don't build w/clang (currently 11). note that azure matrix vars like this _must_ be all caps to register.

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfebe5bb4366`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
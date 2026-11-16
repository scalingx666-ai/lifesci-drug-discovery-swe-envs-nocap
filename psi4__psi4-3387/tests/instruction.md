# Issue

**Title:** fix multiple defs for psimrcc for unity builds

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- @fevangelista , I've had significant success speeding up the psi4 build (2-3x) with unity/jumbo builds, but for the psimrcc module I hit some multiple definition errors when it concatenates the files together. This PR is AI's solution. Does it look ok or make you uneasy? Tests pass, but I haven't explored farther.
- It's a one-liner to exempt psimrcc from the unity build at a reproducible but not hefty cost, so that's the easy backup if this PR needs a lot of work. See  for commands to quickly force the unity build if you want to try it out.
- I've run a full test suite with these changes under unity build, and it's clean.

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78faabd95ba0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
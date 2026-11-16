# Issue

**Title:** Enforce Satisfiable TDSCF Convergence

## Description

## Description
Existing Psi's TD-SCF implementation assumes that eigenvalues less than 1e-10 are zero. This blocks arbitrarily tight convergence. We now warn the user if they try to set the convergence tighter than is possible.


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] r_convergence for TD-SCF is now capped at 5e-8. Any tighter thresholds will be raised up to that.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x]  r_convergence for TD-SCF is now capped at 5e-8. Any tighter thresholds will be raised up to that.
- [x] Adds new unit test. This fails on master - Psi tries to converge to a residual of 1e-10 while simultaneously zero'ing out eigenvalues less than 1e-10 when identifying new Davidson vectors to add.
- [x] Needed for GauXC integration PR.  

## AI
- [x] No AI usage

## Checklist
- [x] Tests added for newly working feature

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `258591c1c483`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
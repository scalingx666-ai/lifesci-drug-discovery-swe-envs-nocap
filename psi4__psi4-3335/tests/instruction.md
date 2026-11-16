# Issue

**Title:** Fix potential nullptr dereference in DSYEV_descending

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
DSYEV returns the eigenvalues and optionally eigenvectors sorted in the order of ascending eigenvalues.
DSYEV_descending swaps the order to descending without checking if the eigenvectors have been requested, resulting in a nullptr dereference if not. This PR fixes that corner case.

Thankfully, nothing in the current Psi4 codebase seems to be using this particular combination of "only eigenvalues, descending order", so the impact should be only on out-of-tree codes using Matrix::diagonalize with that particular setting.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] PSI_API: fixed corner case in `Matrix::diagonalize`, no longer dereferences a nullptr if `nMatz == evals_only_descending`

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Make sure the eigenvector pointer is not nullptr before trying to swap its elements in DSYEV_descending

## Checklist
- [x] No new features
- [x] Tests run by CI are passing

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73d3f5b48cf5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
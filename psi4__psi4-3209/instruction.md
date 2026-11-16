# Issue

**Title:** Opt options

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Adds optking keywords missed in #3204. For users, if these options are needed with an older version of Psi4, they can be passed through `psi4.optimize(..., 'optimizer_keywords'=)` to optking. Features require `optking >= 0.3.0`

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] Adds shortcut for freezing all dihedrals in a molecule `freeze_all_dihedrals` and `unfreeze_dihedrals` 

## Checklist
- [x] Ran -L opt subset
- [x] keywords checked explicitly in optking's tests  

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `82ce59501248`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
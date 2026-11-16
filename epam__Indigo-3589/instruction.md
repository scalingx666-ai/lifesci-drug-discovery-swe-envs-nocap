# Issue

**Title:** #3524 – Support default InChI (Key) generation

## Description

## General description of the PR:

Fix for #3524.
Added optional parameter to force InChI generation parameters.

## Generic request
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name does not contain '#'
- [x] base branch (master or release/xx) is correct
- [ ] PR is linked with the issue
- [ ] task status changed to "Code review"
- [ ] code follows product standards
- [ ] regression tests updated
### For release/xx branch
- [ ] backmerge to master (or newer release/xx) branch is created
### Optional
- [x] unit-tests written
- [ ] documentation updated

## Backmerge request
- [ ] PR name follows the pattern `Backmerge: #1234 – issue name`
- [ ] PR is linked with the issue
- [ ] base branch (master or release/xx) is correct
- [ ] code contains only backmerge changes

## Bump request
- [ ] PR name follows the pattern `Bump version to ...`
- [ ] add brackets \[ \] for 'skip ci' and put it into the body
- [ ] milestone is linked to PR
- [ ] all tickets are closed inside the relevant milestone

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cebeb9c1f393`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
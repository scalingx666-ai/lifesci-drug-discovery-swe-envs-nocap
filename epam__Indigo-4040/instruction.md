# Issue

**Title:** Bump to version 1.51.0-dev.1

## Description

[no ci]

## Remove-me-section
* Notify reviewers about the pull request
* Keep only necessary sections below for the review

## Generic request
- [ ] PR name follows the pattern `#1234 - issue name`
- [ ] branch name does not contain '#'
- [ ] base branch (master or release/xx) is correct
- [ ] PR is linked with the issue
- [ ] task status changed to "In Review"
- [ ] code follows product standards
- [ ] regression tests updated
### For release/xx branch
- [ ] backmerge to master (or newer release/xx) branch is created
### Optional
- [ ] unit-tests written
- [ ] documentation updated

## Backmerge request
- [ ] PR name follows the pattern `Backmerge: #1234 - issue name`
- [ ] PR is linked with the issue
- [ ] base branch (master or release/xx) is correct
- [ ] code contains only back merge changes

## Bump request
- [ ] PR name follows the pattern `Bump version to ...`
- [ ] add brackets \[ \] for 'skip ci' and put it into the body
- [ ] milestone is linked to PR
- [ ] all tickets are closed inside the relevant milestone

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `864b786b0145`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
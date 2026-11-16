# Issue

**Title:** #3691: PtrArray hybrid contract implementation

## Description

This is first PR from container refactoring Milestone. Tightens PtrArray<T> API contract on top of #783 baseline, while keeping source compatibility for existing call sites via [[deprecated]] overloads that delegate to the new owning overloads (DRY + strong exception safety).

## Remove-me-section
* Notify reviewers about the pull request
* Keep only necessary sections below for the review

## Generic request
- [ ] PR name follows the pattern `#1234 – issue name`
- [ ] branch name does not contain '#'
- [ ] base branch (master or release/xx) is correct
- [ ] PR is linked with the issue
- [ ] task status changed to "Code review"
- [ ] code follows product standards
- [ ] regression tests updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9f2599fb449`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
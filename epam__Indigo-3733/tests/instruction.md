# Issue

**Title:** #3702 - Unfold hydrogens makes monoradical from Helium with odd valence

## Description

Fix helium elctron count. Add UT

## Generic request
- [ ] PR name follows the pattern `#1234 – issue name`
- [ ] branch name does not contain '#'
- [ ] base branch (master or release/xx) is correct
- [ ] PR is linked with the issue
- [ ] task status changed to "Code review"
- [ ] code follows product standards
- [ ] regression tests updated
### For release/xx branch
- [ ] backmerge to master (or newer release/xx) branch is created

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2df87c0a84cd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
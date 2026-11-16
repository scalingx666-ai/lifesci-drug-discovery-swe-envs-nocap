# Issue

**Title:** Ghost atom and ECPs bug fix

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Fix for the bug described in  about incorrectly loading ECPs for ghosted atoms.


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] Calculations using ghosted atoms that contain ECPs in the basis set can now be executed properly.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] When loading basis functions we check if we should skip loading ECPs (`skip_ghost_ecps`) and if `true` then we check if an atom is a ghost (`mol->Z(atom) == 0.0`). If yes we do not load ECPs fot it.
- [x] Added optional boolean argument `skip_ghost_ecps` for `construct_basisset_from_pydict` function. The default is `true`, we set it `false` for atomic calculations (like SAD guess).

## Questions
- [x] Are the check runs failing due to the changes in this PR?

## Checklist
- [x] Minimal working example
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e54962d6294`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
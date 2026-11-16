# Issue

**Title:** Add access to lowdin spins

## Description

## Description
The per atom spin is calculated and printed to the psi4 output file, but not accessible as a property. This PR provides a property to retrieve that value.
Written with @bennybp 


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- Provide "lowdin_spins" property to users.

## Questions
- [x] Is there a was to have both properties returns when only the "lowdin_charges" keyword is provided?

## Checklist
- [ ] Tests added for any new features
- [ ] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [ ] Ready for review
- [ ] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e18dcde1269`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
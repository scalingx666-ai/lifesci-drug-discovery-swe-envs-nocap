# Issue

**Title:** Disallow MBIS with ECPs

## Description

## Description
I think , so correcting the number of electrons being passed to MBIS won't solve the issue. An error should be raised for all ECPs.

~Fix MBIS charge partitioning for systems with Effective Core Potentials (ECP). When ECP basis sets are used, PSI4 modifies `mol->Z()` to store the effective nuclear charge (valence protons only). MBIS was incorrectly using this modified value for both shell counting and proatom parameter lookup, causing it to fetch wrong atomic model parameters. The fix uses `mol->true_atomic_number()` (element identity) instead of `mol->Z()` (effective charge) at two key locations.~

Close #3135 

## User API & Changelog headlines
- [x] MBIS raises an error for Effective Core Potentials

## Dev notes & details
- [x] Added regression test `tests/mbis-ecp/` validating MBIS on CaH⁻ with def2-svp basis (includes ECP)
- [X] Updated `tests/mbis-7` with a basis set that doesn't have an ECP
- [X] Maintainers of `denspart` have clarified that MBIS is for all electrons only unless you recontruct the electron density of an ECP which `psi4` does not support. 

## Questions
- None

## Checklist
- [X] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6abcd0fe717e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
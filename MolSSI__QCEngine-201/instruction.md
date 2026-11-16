# Issue

**Title:** psi4 windows version and outfile psiapi mode

## Description

<!-- Thank you for your contribution! -->

## Description
Fixes in conjunction with psi4 ddd. Still needs printing cleared out, after I confirm working.

## Changelog description
- [x] Switch `psi4 --version` collection to only grab the last line. This should fix #200, but I can't say for sure because chocolatey is down _again_.
- [x] Use an independent tmpdir for each psi4 run in psiapi mode, not just exe.
- [x] Reset the scratch dir for psi4 in psiapi mode, so `set guess read` in distributed driver has a chance.
- [x] Add a connection to a `postclean` kwarg to cleanup the qcschema_tmpfile at end of routine (suitable for psiapi) rather than at atexit

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [ ] Ready to go SQUASH!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95a6759e15fc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
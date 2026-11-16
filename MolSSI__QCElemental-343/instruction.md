# Issue

**Title:** add hashes and rearrange mult handling

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR is preparatory to #318.

- [x] NEW: adds a check to the basic Molecule pydantic model so multiplicities <1 get caught. This route is accessed when `Molecule(..., validate=False)`. I believe this is a universally good check, but it is a new restriction. Any weird positron, fractional electron, etc. reason to not catch less-than-one mult?
- [x] add many hash checks (incl. all the chgmult variations in `validate_and_fill_chgmult` testing) to molecules, so we'll know if code starts changing the hash and thereby disrupting the QCA server.
- [x] `qcel.molparse` has a different error message for less-than-one `fragment_multiplicities` you try to put through it. `qcel.molparse` is accessed whenever `Molecule(...)` or `Molecule(..., validate=True)` is called.
- [x] `qcel.molparse` newly allows floats that are ints (e.g., `1.0`) for multiplicity. previously it would raise an error about not being an int.
- [x] `qcel.molparse` newly has a dedicated error for any less-than-one `molecular_multiplicity` you try to put through it. Previously it raised the usual "Inconsistent" error.
- [x] more tests that chgmult are processing as expected, including some with fractional _charges_ () for the first time.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `859c0838703f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
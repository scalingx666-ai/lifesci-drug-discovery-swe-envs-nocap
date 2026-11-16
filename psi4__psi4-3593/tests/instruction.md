# Issue

**Title:** QCSchema: serialize symmetry-blocked qcvars per irrep

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
With stability_analysis on a symmetric UHF molecule, SCF STABILITY EIGENVALUES has one block per irrep, so run_qcschema failed after a converged SCF (through QCEngine: InputError).

_serial_translation called .np on every Matrix/Vector qcvar, which raises ValidationError ("Attempted to call .np on a Psi4 data object with multiple irreps") for symmetry-blocked data.

Blocked Matrix/Vector values are now returned as one entry per irrep, in the molecule's irrep order: numpy blocks, or flattened lists for JSON. Single-irrep data is unchanged.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- Fix serialization of stability analysis into QCSchema extras/qcvars

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [ ] Feature1
- [ ] Feature2

## Questions
<!-- Any questions or decision points on which you need clarification
     from the Psi4 team. -->
- [ ] Question1

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [X] Assisted-by claude-code/2.1.295:claude-opus-5-5 - debugging, code, and tests

## Checklist
- [X] Tests added for any new features
- [ ] Docstring or narrative docs/sphinxman/source updated if needed
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [X] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `944e969d049f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
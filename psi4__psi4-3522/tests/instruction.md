# Issue

**Title:** Add some CDJK regression tests

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
CDJK has some testing gaps that allowed the weird behavior fixed in #3500 to persist unnoticed.
This PR adds pytests that would have failed prior to PR #3500, and adds a note to the docs about CD not supporting out-of-core.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- None

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Test that SCF_TYPE=CD rejects an unsupported SCF_SUBTYPE, such as OUT_OF_CORE, YOSHIMINE_OUT_OF_CORE, REORDER_OUT_OF_CORE, and throws with CDJK's message.
- [x] Test that SCF_TYPE=CD fails with the correct messages if there is insufficient memory
- [x] Test that reading cached Cholesky vectors back off disk (DF_INTS_IO=LOAD) works in low-memory scenarios.

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [x] `test_cdjk.py`, the file containing the new tests is entirely LLM-generated

## Checklist
- [x] The PR adds new tests to better cover CDJK
- [x] Note about CD limitation added to docs and the SCF_SUBTYPE docstring.
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e8935afcf3df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
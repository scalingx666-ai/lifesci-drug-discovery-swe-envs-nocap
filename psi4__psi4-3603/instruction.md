# Issue

**Title:** Drop Python 3.10

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] If you want to build Psi4 from source with Python 3.10, it's compatible at the moment. But since it's end-of-life, it's harder to install and we're no longer supporting it.

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- ~AI usage~

## Checklist
- ~Tests added for any new features~
- ~Docstring or narrative docs/sphinxman/source updated if needed~
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91dc3011b82c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
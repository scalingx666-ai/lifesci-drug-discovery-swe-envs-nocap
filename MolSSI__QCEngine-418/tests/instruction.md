# Issue

**Title:** overhaul psi4 detection parsing

## Description

<!-- Thank you for your contribution! -->

## Description
The existing psi4 detection has worked great when psi4 is in order and conda environments prevail, but #389 and #292 show that if something is set up a little wrong with psi4, then everything devolves into an IndexError with the existing psi4 detection.

This PR improves matters by
* in the complete-the-psithon-psiapi-pair blocks:
  * only doing string-safe operations on stdout
  * forming clearer error responses
  * catching stderr instead of tossing it and parsing stdout anyways
  * getting rid of `env` passing. As @Flamefire pointed out, the psi4 module is already in sys.path or which_import wouldn't have worked. unlike #389, code is now passing no env so current env is used (and can provide numpy, etc.). I've tested that there's no need to provide env=os.environ to get current env.
  * checking returncode
  * it was also not showing error messages when psithon found but not psiapi b/c final check was of psithon only. now checking at the weak point
* in the version fn:
  * only doing string-safe operations on stdout
  * catching stderr instead of tossing it and parsing stdout anyways
  * checking returncode

Hopefully this will be more robust.   

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `034fd1a179e5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
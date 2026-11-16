# Issue

**Title:** Improve CDJK object

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR is a collection of modest improvements to the CDJK object, modernizing a few things, adding missing docstrings and improving the robustness of how the unimplemented range-separated (wK) exchange is refused.
The PR also reduces the exposure of `CDJK::cholesky_tolerance_` and `CDJK::ncholesky_` from protected to private, marks `CDJK::cholesky_tolerance_` as `const`, and deprecates `CDJK::cderi_` as a member variable.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] PSI_API changes: `CDJK::cholesky_tolerance_` and `CDJK::ncholesky_` are now private instead of protected, `cholesky_tolerance_` is now `const`.
- [x] PSI_API change: CDJK now overrides `set_do_wK` and throws in it if the unimplemented range-separated (wK) exchange is requested.
- [x] PSI_API deprecation notice: `CDJK::cderi_` is planned to be moved inside `CDJK::initialize_JK_core`. Unless someone speaks up, 1.11 will be the last release to have it.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Remove redundant `using namespace psi` from CDJK.cc
- [x] Instead of having an empty dtor definition, declare it to be the default dtor and add an explanation why deleting the dtor declaration would be undesirable.
- [x] Assert that `do_wK` must be false for CDJK in its setter, `set_do_wK`, instead of relying on users to call `print_header()`
- [x] Modernize uses of `PsiException("msg", __FILE__, __LINE__)` to the more concise `PSIEXCEPTION("msg")`. This should also make the eventual switch from ` __FILE__, __LINE__` to C++20's `std::source_location` easier, whenever that happens.
- [x] Simplify how the error is thrown for unknown SCF Type
- [x] Add proper Doxygen docstrings to `cholesky_tolerance_` and `ncholesky_`. Update and expand docstrings for the CDJK ctor and dtor, with explanations of why things are the way they are.

## Checklist
- [x] No new features
- [x] Tests run by the CI are passing

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `500081ebb925`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
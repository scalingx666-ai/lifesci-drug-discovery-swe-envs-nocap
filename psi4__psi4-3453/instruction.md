# Issue

**Title:** Finish moving CDJK::cderi_ into initialize_JK_core

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR is a , moving `CDJK::cderi_` into `CDJK::initialize_JK_core`. This reduces the scope and lifetime of this implementation detail, narrows PSI_API, saving a little bit of memory, and making sure that we don't have an integral engine outliving the `IntegralFactory` it carries a pointer for.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] PSI_API change: `CDJK::cderi_` was deprecated in 1.11 and is now removed from the C++ API.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Finalize moving `CDJK::cderi_` from being a protected member of `CDJK` to a local in `CDJK::initialize_JK_core`
- [x] Adjust how `cderi` is initialized. The `IntegralFactory` does not need to be held by a `shared_ptr`, and `cderi` can be shallow-const.
- [x] Add/adjust comments/TODOs for `memory_estimate` functions in the JK hierarchy. Since we are moving towards linear-ish scaling correlation methods, "O(N^2) memory is negligible, return 0" type of approximations would be nice to tidy up.

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [x] LLMs were consulted regarding the new `cderi` init, and the comment about making `memory_estimate` `const` requiring `DFHelper` and `MemDFJK` refactoring is based on LLM output.

## Checklist
- [x] No new features.
- [x] No docs update needed
- [x] Tests run by the CI are passing.

## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1af240f9e203`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
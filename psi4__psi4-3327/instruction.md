# Issue

**Title:** Nit: do not use double underscores at the beginning of incude guard names

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Symbols beginning with 2 underscores are reserved for the C++ implementation.
While this is unlikely to cause any issues, they should not be used as include guards.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] Plugin API: plugin.h now defines `PSI4_LIBPLUGIN_PLUGIN_H` as its include guard, instead of `__psi4_src_lib_libplugin_plugin_h`

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Change all include guards that start with double underscores

## Checklist
- [x] No new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [X] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b6812d864a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
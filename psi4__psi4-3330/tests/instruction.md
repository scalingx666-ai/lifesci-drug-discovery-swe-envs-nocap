# Issue

**Title:** Fix redundant LibXC build caused by GauXC's ExchCXX dependency handling

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Currently, when GauXC is enabled at build time, the Psi4 build system builds it from source, but GauXC's build system then needs ExchCXX and the build of ExchCXX always ends up building its own copy of LibXC, even if a suitable binary package for LibXC has already been found by Psi4's CMake. This slows down any CI lanes where GauXC is enabled, and contributes to the intermittent CI failures due to timeouts on the lanes which enable GauXC.

This PR fixes the issue by passing the path to LibXC to the GauXC build system.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] Building from source with GauXC enabled should be faster if GauXC is built from source but a suitable LibXC binary is found in the environment.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Pass STAGED_INSTALL_PREFIX in CMAKE_PREFIX_PATH when building GauXC so the ExchCXX CMake can find the LibXC binaries
- [x] Bump LibXC version pin to latest (fix did not work with old version)
- [x] Accommodate GauXC fixing a typo in their API

## Checklist
- [x] No new features
- [x] All CI lanes run

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6053f9aefa46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
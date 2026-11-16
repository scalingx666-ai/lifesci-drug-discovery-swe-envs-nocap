# Issue

**Title:** accommodate pkg_resources decease

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->

### Note: this can hit newly created local environments, too. To fix, either downgrade your setuptools or incorporate these two lines into your psi4 code.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] setuptools 82.0 finally kicked out pkg_resources which we were still using deep under the hood, so update that usage https://setuptools.pypa.io/en/stable/history.html#v82-0-0
- [x] one of the docs extensions also uses it. the docs pkgs are somewhat frozen in the past to accommodate pydantic v1, so pinning that to sub-82 for now

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68ce3444ad66`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add support for verbosity keyword

## Description

### Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR implements and  by adding support for a verbosity keyword which when set to muted will stop temporary files from being made which causes a failure when running many parallel xtb calculations. 

### Changelog description
<!-- Provide a brief single sentence for the changelog. -->
The harness now accepts a `verbosity` keyword which can be a string or int corresponding to the level of verbosity, the accepted strings and associated ints are `full=2`, `minimal=1`, `muted=0`.

### Status
<!-- Please, add tests and documentation for your contribution. -->
Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a6fd5c40b26`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
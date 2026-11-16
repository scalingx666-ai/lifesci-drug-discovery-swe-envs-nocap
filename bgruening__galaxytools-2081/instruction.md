# Issue

**Title:** 3Dtrees standardization: accept las as well as laz input

## Description

<!-- claude-projects-attribution: {"github_login":"kgerb"} -->
_Requested by **Kilian**_

FOR CONTRIBUTOR:
* [ ] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [ ] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

## Summary
- accept `las` as well as `laz` in both modes (single file and collection); the 1.2.1 container already reads `.las`, only the wrapper restricted the input to `laz`
- stage each input under its own extension (`input.${ext}`) so the tool sees the real file type; the standardized output is still written as `input.laz`
- bump the wrapper to `1.2.1+galaxy1` (wrapper-only change, same container)
- add `test-data/micro.las` (16 KB, 397 points, a 5 x 5 m crop of `mikro.laz` with its CRS) and two tests: single-file standardization of a las input, and collection validation of a las input

## Validation
- `planemo lint --report_level all`: clean
- `planemo test --docker --galaxy_branch release_25.1`: 8/8 tests pass (the `las` datatype exists from Galaxy 25.0 on)

## After merge
Install `3dtrees_standardization` `1.2.1+galaxy1` on Galaxy EU so that las uploads are no longer rejected.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6dac2e5c1c0e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
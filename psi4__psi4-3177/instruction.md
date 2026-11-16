# Issue

**Title:** Eliminate casting of Dimension objects to pointers within libmoinfo

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This is the third PR in the `libmoinfo` series, following #3101 and #3155.
Currently, `libmoinfo` is calling the `intvec convert_int_array_to_vector(int n, const int* array)` to initialize some of its `std::vector<int>` members by copying the innards of `Dimension` objects. Unfortunately this is happening through the rather inelegant mechanism of implicitly calling `Dimension::operator const int*() const`, which is set to be removed eventually.

This PR replaces all calls of `convert_int_array_to_vector` in `libmoinfo` with simple assignment-initialization. Now, this could in theory lead to a change in behavior, as the former only copies the first `n` elements of the array inside the Dimension object instead of the entire thing, but in practice that does not seem to be happening. As far as I can tell, for trouble to happen it would require an internally inconsistent `Wavefunction` object or `libmoinfo` trying to use only a subset of the irreps.

Nevertheless, I have added checks to ensure that any condition that would lead to an unpredictable change in behavior after this PR, results in a crash instead. I don't think it should ever happen, but internal consistency checks are probably not a bad idea anyways.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] None

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Replace all calls of `convert_int_array_to_vector` in `libmoinfo` with simple assignment-initialization
- [x] Add internal consistency checks to guard against possible hazards
- [x] Remove now-unused function `MOInfoBase::convert_int_array_to_vector`

## Questions
-  If everyone else is confident that the checks are redundant I _could_ remove them.

## Checklist
- [x] No new features
- [x] No new errors in the full test suite

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b58f7a021b7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
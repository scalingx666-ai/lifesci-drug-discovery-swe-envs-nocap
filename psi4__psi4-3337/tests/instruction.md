# Issue

**Title:** Fixed several memory leaks tied to psimrcc

## Description

## Description
I found some memory leaks in psimrcc. One of them was a cross-dependence between shared pointers that resulted in the wavefunction never being freed. Also patched a few smaller ones. There is still one issue where one set of matrices has values allocated with both new and malloc, so deleting them becomes undefined behavior no matter what I do.


## User API & Changelog headlines
- [ ] Fixed memory leaks related to psimrcc.
- [ ] Fixed a segfault in mcscf that prevented optimizing with psimrcc.

## Dev notes & details
- [ ] Fixed memory leaks related to psimrcc.
- [ ] Fixed deprecation warnings in psimrcc. I may go through some other modules as well if I have time and a lack of patience.
- [ ] Fixed a segfault when optimizing with psimrcc.

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b6812d864a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
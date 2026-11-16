# Issue

**Title:** Libmoinfo rework, part 2

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This is the continuation of my previous MOInfo PR #3112, with the following general themes:

- Adding new docstrings and making existing ones machine readable for VS Code (and probably also Doxygen)
- Rebalancing the class hierarchy by sinking things that get reused to the base class, and hoisting things up in the inheritance chain that only get used in one derived class
- Reducing visible and mutable state, as well as the contact surface of the classes. This is achieved by making data and functions as private as possible, providing access to data through getters returning `const&` when necessary, and making a few data members `const`. Having `const` members in classes is sometimes considered to be bad form, but AFAIK all of the downsides are already incurred on account of `MOInfoBase` having reference members.

The git history on this branch is admittedly a bit messy, I changed my mind about a couple of things. LMK if that is a problem.
The next PR in this series will get to what I originally wanted to achieve and remove uses of the ugly "cast Dimension object to pointer" operators () from `libmoinfo.`

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] No API changes

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Unused function `MOInfoBase::correlate` is removed
- [x] The only thing the `MOInfoBase` dtor does is call `MOInfoBase::cleanup()`, an empty function. Removed both.
- [x] Moved the contents of `MOInfo::free_memory()` into its only caller, the `MOInfo` dtor
- [x] Added a lot of new machine-readable docstrings, moved some existing ones
- [x] Some "obsolete code", commented out a long time ago is deleted from `moinfo_mappings.cc`
- [x] Moved the `double** scf` MO array and the `get_scf_mos()` getter from `MOInfoBase` to `MOInfo` and made the array private
- [x] Moved the contents of `MOInfoBase::startup()` into its only caller, the `MOInfoBase` ctor
- [x] Moved `MOInfoBase::nmo` to `MOInfo` and made it private
- [x] Made the molecular charge `const` and private in `MOInfoBase`
- [x] Made `MOInfoBase::sopi` private, added a protected getter fn to give access in derived classes
- [x] Made `MOInfoBase::nso`, `MOInfoBase::nuclear_energy` and `MOInfoBase::irr_labs` private
- [x] All functions in `MOInfoBase` that have previously returned copies of `std::vector` members now return `const&` to the vector in the object, avoiding a potential copy.
- [x] Since `MOInfoBase::silent` is only used in the ctor of `MOInfo,`, I removed it from `MOInfoBase` and `MOInfoSCF`
- [x] Inlined `MOInfo::get_actv(size_t i)` and `MOInfo::get_docc(size_t i)` as both were only called once. Since these overloads are now gone from `MOInfo`, it can now just use `get_docc()` and `get_actv()` from `MOInfoBase` instead of having to reimplement or explicitly inherit them.

## Checklist
- [x] No new features
- [x] Tests run by the CI are passing
- [x] Errors in the full test suite appear to be unrelated to `libmoinfo`

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf9d20fc5799`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
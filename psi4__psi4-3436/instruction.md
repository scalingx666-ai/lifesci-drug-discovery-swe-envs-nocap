# Issue

**Title:** Mark the Python exports of Options::set_read_globals and Options::set_read_globals as deprecated

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
`edit_globals_` is a private `bool` mode flag in the `Options` class. The reason it exists it that `Options` objects keep options in two separate stores:

- globals_:  a single flat `map<string,Data>` the global keyword table.
- locals_: a map<string, `map<string,Data>>` keyed by module name, so each module (SCF, CCENERGY, DFMP2, …) has its own private option table

`edit_globals_` is the flag that decides which of those two stores the option machinery reads from and writes to. It is only ever turned on transiently, when Psi4 starts up, during `clean_options()` and if a plugin is being loaded. Its public face is the getter `read_globals()` and the setter `set_read_globals(bool)`. This is all fine, but these are also currently part of the Python API, which is probably not needed and in case of the setter, slightly dangerous.

To use `set_read_globals` correctly one has to call it to set it to `true`, do whatever has to be done on the globals, and then call it again with false to restore the `Options` object to its normal state. If a Python caller sets it true and never resets it (perhaps because an exception is thrown and handled before the reset) the options object is left silently corrupted, and mayhem ensues.

There is nothing in the Psi4 tree currently that is using these Pybind11 exports, so unless someone likes having these in for debugging or prototyping stuff, IMO it would be best to deprecate and remove them. A pure-Python plugin might conceivably want to inject options into the global space the same way the C++ plugin loader does, and that would need these exports, but I am not aware of anyone doing that.

Since these are not really acute problems, I am setting the deprecation time horizon to 1.12. Hopefully that will be enough time for any downstream users of the Python API to notice the deprecation messages.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] Python API: The Python API export of `Options::set_read_globals(bool)` is now deprecated due to disuse and because it is slightly hazardous. Unless someone speaks up, 1.12 will be the last release to have it.
- [x] Python API: The Python API export of `Options::read_globals()` is deprecated due to disuse and to better hide C++ implementation details. Unless someone speaks up, 1.12 will be the last release to have it.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Add a universal deprecation helper to driver/p4util/python_helpers.py
- [x] Add deprecation notices for `Options.read_globals()` and `Options.set_read_globals(bool)`

## Checklist
- [x] No new features
- [x] Tests run by the CI are passing

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `500081ebb925`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
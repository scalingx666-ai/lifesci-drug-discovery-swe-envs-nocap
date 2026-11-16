# Issue

**Title:** Fix cursor position in text files and add unwrapped property to LAMMPS

## Description

This  by adding the frame property `is_unwrapped` to the LAMMPS trajectory reader. This boolean property is always set when reading.
Also, this  (at least for text files) by advancing the cursor before reading (and parsing) of a frame. It's possible to read the next frame after an (parsing) exception, as long as the initial scanning of frame offsets works without an error.
As stated in the issue, I think this is most important for text files because they can be easily edited by hand which may introduce inconsistencies.

Additionally, there are some minor changes to suppress compiler warnings. Notably, Clang doesn't like the string literal `_sv`, so this option is disabled in the cmake config.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f46c5d50164f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix static builds with maeparser

## Description

This reverts a change that was done in PR #9030, when the nanobind wrappers were added.

Before that patch, instead of including `maeparser/Writer.hpp`, we forward declared the `schrodinger::mae::Writer` class, but in that patch we replaced the forward declaration with an include.

This is a problem when RDKit is built statically with maeparser being built locally as part of the RDKit build (i.e. maeparser is not provided as an external dependency). In such scenario, the maeparser headers are not installed along RDKit. This means that any 3rd party code that uses this static RDKit build and tries to include `MolWriters.h` will fail to build due to `maeparser/Writer.hpp` being missing.

This patch restores the forward definition (so that the header isn't required when `MolWriters.h` is included), and pushes the include to the nanobind wrapper file, the same way it is included in the Boost Python wrappers.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24b68ec319e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
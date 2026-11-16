# Issue

**Title:** Add a Jaguar harness

## Description

<!-- Thank you for your contribution! -->

## Description
Add a Jaguar harness that can implements the standard `energy`, `gradient`, and `hessian` drivers. The harness is registered in both the standard suite and the alignment tests. The harness relies on the Schrodinger Suite tools, namely `JaguarInput` (for generating an input file from a qcschema) and `JaguarOutput` (for parsing properties from the output, to generate an  `AtomicResult`).

Incidentally, I also sped up the testing utility `is_program_new_enough`, which previously searched the PATH for all registered programs, even though it just needs to check if the specific program is installed/compatible.

## Changelog description
Add a harness for running Schrodinger's Jaguar QM program

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go
- [x] Jaguar related tests pass for me locally with my Schrodinger suite installation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e04e381c0e41`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
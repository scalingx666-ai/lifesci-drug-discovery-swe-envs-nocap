# Issue

**Title:** Add adcc harness

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR adds a harness for [adcc](https://adc-connect.org/v0.15.1/index.html), a Python-driven toolkit for excited states within the algebraic-diagrammatic construction scheme for the polarization propagator.

`adcc` requires an SCF driver to run first (e.g. Psi4, pyscf) to provide the SCF reference state, integrals, etc. throughout the rest of the computation.

CC @mfherbst

## ToDo

- [x] robust SCF wrapper
- [x] proper input keyword handling (including defaults etc.)
- [x] error handling
- [x] add tests

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Add a harness for [adcc](https://adc-connect.org/v0.15.1/index.html)

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6adbccc2a3d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
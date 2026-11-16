# Issue

**Title:** Convert OptimizationResult.input_data to the requested version in convert_v

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
v2 OptimizationResult.convert_v always converted the nested input_data with convert_v(1), even when the target was QCEL_V1V2_SHIM_CODE. On Python 3.14, where QCSchema v1 models cannot be instantiated, converting an optimization result to the v1v2 shim therefore failed with "QCSchema v1 model 'Molecule' cannot be instantiated". QCFractal's compute workers do exactly this conversion, so every optimization they ran on 3.14 errored.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `bash scripts/format.sh` in the base folder or use pre-commit. -->
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7828af830a1f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
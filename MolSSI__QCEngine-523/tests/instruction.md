# Issue

**Title:** Fall back to _v1v2 shim for QCSchema v1 procedure dicts on Python 3.14

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
On Python 3.14, pydantic.v1 is unavailable and qcelemental's v1 models raise RuntimeError on instantiation. ProcedureHarness._build_model built QCSchema v1 dict inputs (e.g., OptimizationInput from QCFractal) with the v1 model, so every geometric/berny/optking optimization given a v1 dict failed, even with return_version=2.

Mirror the existing AtomicInput fallback in programs/model.py: if the v1 model cannot be constructed, build the input with the qcelemental.models._v1v2 shim (when one exists for that model) and immediately convert to v2. Models without a shim (e.g., TorsionDriveInput) still raise the original error.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `edaa7c7af97f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
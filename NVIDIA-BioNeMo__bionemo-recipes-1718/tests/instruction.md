# Issue

**Title:** fix(ci): repair nightly recipes failure (run 32352727491)

## Description

## Nightly CI Repair

**Workflow:** unit-tests-recipes.yml (ID: 182833798)
**Failed Run:** https://github.com/NVIDIA-BioNeMo/bionemo-recipes/actions/runs/32352727491
**Failing SHA:** 648f4d983392d0c38f2d2da18dea0479cdc650b2

### Root Cause
Unconstrained `megatron-core` resolved to 0.19.0 after the 26.07 CI update, incompatible with pinned NeMo 2.4.0. The geneformer model depends on `nemo_toolkit[lightning]==2.4.0` which requires megatron-core==0.17.1.

### Fix
Pin `megatron-core==0.17.1` in `models/geneformer/pyproject.toml` to match the version validated in the model's CI bootstrap script (`.ci_build.sh`).

### Changes
- `models/geneformer/pyproject.toml`: pin `megatron-core==0.17.1`

### Tests
- TOML parse and dependency-pin assertion: passed
- `git diff --check`: passed
- Pre-commit checks on changed file: passed

### Verification
- Commit signed with SSH key (verified: true, reason: valid)
- Signed-off-by trailer present

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `648f4d983392`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
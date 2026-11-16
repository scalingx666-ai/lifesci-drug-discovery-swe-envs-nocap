# Issue

**Title:** fix(geneformer): resolve protobuf conflict with nvidia-resiliency-ext>=0.6.0

## Description

## Problem

The geneformer nightly CI fails because megatron-core==0.17.1 asserts nvidia-resiliency-ext>=0.6.0 at import time, but that version isn't installed in the CI container.

Simply adding nvidia-resiliency-ext>=0.6.0 to pyproject.toml creates an unresolvable pip conflict:
- nvidia-resiliency-ext 0.6.0 → grpcio-tools>=1.76.0 → protobuf>=6.30.0
- nemo-toolkit==2.4.0 → protobuf~=5.29.5

## Fix

Add a `.ci_build.sh` that installs nvidia-resiliency-ext>=0.6.0 with `--no-deps` (skipping grpcio-tools which is not needed for test execution), then installs the package normally.

The CI workflow already supports `.ci_build.sh` as a hook — if the file exists, it runs that instead of the default `pip install -e .`.

## Root Cause

nvidia-resiliency-ext 0.6.0 added grpcio/grpcio-tools as hard dependencies (for its new gRPC-based fault tolerance features), but these are incompatible with nemo-toolkit 2.4.0's protobuf pin. This will resolve when nemo-toolkit relaxes its protobuf constraint.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f9a946be71d3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** fix(evo2_megatron): pin warp-lang<1.13.0 in Dockerfile

## Description

## Problem

`subquadratic-ops` is incompatible with `warp-lang>=1.13.0`. The Dockerfile picks up the latest warp, causing build failures.

## Fix

Add `RUN uv pip install "warp-lang<1.13.0"` to the Dockerfile after venv creation. Temporary workaround until subquadratic-ops gets a warp 1.13-compatible release.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5497faa6ea71`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Csse pyd2 510 Part 2

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
* ~currently atop #347~
- [x] pick over remaining relevant parts of @Lnaden #321 (below), then patch 'em up. so first commit is from #321 (note not a literal cherry-pick like #347) and second commit a1f7dcc are the fixes to get it working.
- [x] Fix up `DFTFunctional`, `CPUInfo` to be pydantic v2 API only. (afaik, this was an effort that didn't go anywhere. they're not used in qcng. Anyone know of usage in the wild downstream?)
- [x] Fix up `Datum` to be pydantic v2 API only. This is well-used, esp for NIST physical constant, but afaik it's never within a QCSchema model, so safe to support only one version.
- [x] Fix up serialization of models. Tentatively, trying an in-class try/except/try/except to handle serializing both pyd v1 and v2 API models. It works for tests, but we'll see about real life.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [x] Code base linted
- [x] Ready to go
- DON'T SQUASH

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c219aa272f72`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
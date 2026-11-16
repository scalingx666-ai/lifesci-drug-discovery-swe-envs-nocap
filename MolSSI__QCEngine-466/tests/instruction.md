# Issue

**Title:** add plain qcmanybody harness

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Bulk of #448 . Adds QCManyBody as a procedure and lets it call QCEngine programs for its inputs. This allows interaction energies or many-body expansions to arbitrary order with none, counterpoise, or VMFC basis set superposition error corrections.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `879205ac46d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
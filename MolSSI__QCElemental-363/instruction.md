# Issue

**Title:** Csse layout opt/td

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
- [x] Unlike previous PRs that changed one field at a time in Atomic<> schema (has a large footprint in QCEngine), this does the more extensive rearrangement of Opt<> and TD<> schemas all at once (albeit small footprint in QCEngine).
- The changelog is overdetailed and unorganized at this point. A easier way (for some) to see the planned changes is in this  figure, where v1/v2 pairs of Atomic<>, Opt<>, TD<> schemas are shown with old/new fields aligned.

[QCSchema_models_wide2_12Dec_cean.pdf](https://github.com/user-attachments/files/18128276/QCSchema_models_wide2_12Dec_cean.pdf)

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c7597c39bce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add JOSS paper for SMACT v4

## Description

## Summary

- Adds JOSS paper (`joss/paper.md` and `joss/paper.bib`) describing SMACT v4
- Updates README and logo for v4
- Includes all author contributions and affiliations

## Changes

- `joss/paper.md` — JOSS manuscript with summary, statement of need, state of the field, new features, and author contributions
- `joss/paper.bib` — bibliography
- `joss/paper.pdf` — rendered PDF for review
- Updated README with v4 features and package structure diagram
- Replaced SMACT logo with v4 version

## Test plan

- [x] Verify PDF renders correctly via `docker run --rm --volume $(pwd)/joss:/data openjournals/inara -o pdf paper.md`
- [x] Check all author ORCIDs and affiliations are correct
- [x] Review bibliography entries

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

* **Documentation**
  * Revised SMACT acronym and screenshots; added a package‑structure diagram and clarified capabilities including mixed‑valence support and updated ICSD‑2024 oxidation‑state data; introduced a property‑prediction module with pretrained composition→property models and a ROOST band‑gap predictor; reframed utils as a submodule and formatted developer commands in fenced bash blocks; expanded manuscript (SMACT v4) with metadata, author ORCIDs, DOIs for references, AI usage disclosure and detailed feature descriptions.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f2f777f6fd49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
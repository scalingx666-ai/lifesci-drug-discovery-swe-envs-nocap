# Issue

**Title:** docs: sharpen JOSS paper wording

## Description

Ongoing PR for paper wording fixes as they come up in review — will add more commits here rather than opening new PRs each time.

## This commit

Splits a run-on sentence in the Statement of Need that spliced three separate ideas together with a semicolon:

> The stages share a common representation of compositions and oxidation-state-resolved species, so screening output can be passed on to structure, property or dopant prediction as the question requires, and of the four only structure prediction requires structural input, in the form of the parent structures it substitutes into; a campaign can therefore narrow a chemical space before incurring any structural cost.

becomes:

> The four stages share a common representation of compositions and oxidation-state-resolved species, so screening output can flow directly into structure, property or dopant prediction. Only structure prediction requires structural input — the parent structures it substitutes into — so a campaign can narrow the chemical space before incurring any structural cost.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

* **Documentation**
  * Revised the JOSS paper’s Statement of Need and State of the Field sections.
  * Condensed descriptions of dopant and property prediction capabilities, including references to available tools and a pre-trained ROOST model.
  * Normalised citation formatting.

* **Legal**
  * Added third-party licensing and attribution notices for bundled material, including the associated source and publication details.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1103d5a24692`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
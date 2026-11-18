# Issue

**Title:** docs: improves documentation and gives better examples for the sugar-related endpoints

## Description

This pull request updates the sugar detection and removal tool endpoints and their documentation to improve clarity, accuracy, and consistency in both the API and its OpenAPI schema. The changes focus on refining endpoint summaries, docstrings, response descriptions, and example data, as well as clarifying the outputs and default behaviors.

Changed the default value for the `extract_linear_sugars` query parameter in the aglycone and sugar extraction endpoint from `True` to `False`, and updated its description to match.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67543a3c5c7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** feat: adds method, endpoint, and test for getting aglycone and sugar atom indices

## Description

This pull request adds a new API endpoint for extracting the atom indices of aglycone and sugar moieties from a molecule, alongside supporting code and tests. The changes include implementing the extraction logic, integrating it into the FastAPI router, defining a response schema, and adding tests for the new endpoint.

**New API functionality for extracting aglycone and sugar atom indices:**

* Added the `get_aglycone_and_sugar_indices` function to `sugar_removal.py`, which extracts and returns the atom indices of aglycone and sugar moieties from a molecule using configurable parameters.
* Registered a new `/get-aglycone-and-sugar-indices` GET endpoint in the FastAPI router (`tools.py`) that exposes this functionality with detailed query parameters and OpenAPI documentation.
* Imported the new function and response schema into the router module for integration. [[1]](diffhunk://#diff-8f75c9bfdad65e9bca362b8e689e4ea3476994cc4bc3649915e773ca5a23cf3aL9-R9) [[2]](diffhunk://#diff-8f75c9bfdad65e9bca362b8e689e4ea3476994cc4bc3649915e773ca5a23cf3aL20-R20)

**Schema and testing:**

* Defined a new Pydantic response model `GetAglyconeAndSugarIndicesResponse` in `tools_schema.py` to standardize and document the API response.
* Added a parameterized pytest test for the new endpoint to ensure correct behavior for both valid and invalid inputs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a371418b5d15`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
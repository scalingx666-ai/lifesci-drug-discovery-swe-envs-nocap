# Issue

**Title:** feat: revises existing sugar removal functionalities and adds new sugar detection functionalities

## Description

This pull request introduces several updates related to sugar removal and extraction functionality, including dependency updates, schema enhancements, and expanded test coverage. The key changes are grouped below by theme.

**Dependency and Toolkit Updates:**

* Updated the `cdk` and `SugarRemovalUtility` JAR dependencies in `setup_jvm()` to use newer versions (`cdk-2.11` and `SugarRemovalUtility` v1.6) for improved functionality and bug fixes.

**Schema and API Enhancements:**

* Added a new Pydantic response model `ExtractAglyconeAndSugarsResponse` in `tools_schema.py` to standardize API responses for extracting aglycone and sugars, including schema examples.
* Improved the docstring for the `GetCircularandLinearSugarResponse` schema to clarify that the output contains SMILES without circular and linear sugars.

**Test Coverage Improvements:**

* Added a new test `test_extract_aglycone_and_sugars` to verify the API endpoint for extracting aglycone and sugars, including both valid and invalid input cases.
* Updated expected outputs in `test_remove_linear_sugars` and `test_remove_circular_sugars` to match revised logic or output format. [[1]](diffhunk://#diff-f3683dff05cb4598fb6c165222bd8cf842baa4dae5bc081b5ef402ae948633cfL133-R133) [[2]](diffhunk://#diff-f3683dff05cb4598fb6c165222bd8cf842baa4dae5bc081b5ef402ae948633cfL154-R154)

**Minor Code Improvements:**

* Refactored the construction of the `group_data` dictionary in `get_ertl_functional_groups` for improved readability and robustness.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75fb97a05323`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
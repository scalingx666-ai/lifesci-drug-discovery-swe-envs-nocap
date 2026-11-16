# Issue

**Title:** feat: async endpoint testing in test command

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [ ] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description**
- This pull request introduces asynchronous model testing capabilities to the Ersilia publishing workflow and refactors how model column information is loaded. The main changes include new async output checks, supporting async API endpoints, and improved result validation logic. Additionally, the model runner and IO services are updated to support async operations, and column information is now loaded via a specialized class for better maintainability.

**Async model testing and output validation:**

* Added `check_simple_model_async_output` method to `CheckService` for validating async model outputs, including new helper methods for result validation (`_results_are_valid`, `_row_has_missing_values`).
* Implemented async API result submission and polling in `IOService` using `aiohttp` and `asyncio`, with a new `submit_smiles_and_get_results` method.

**Model runner and workflow updates:**

* Introduced `serve_model` method in `ModelRunner` to start model serving for async tests; updated `_perform_surface_check` to run both sync and async checks, and added new table/reporting logic for async outputs. [[1]](diffhunk://#diff-82fa881a1c189eacfc2a0f2129d0b675d3345ccadd8c70960e7bedbc2c6b4d4fL127-R148) [[2]](diffhunk://#diff-82fa881a1c189eacfc2a0f2129d0b675d3345ccadd8c70960e7bedbc2c6b4d4fR726-R738) [[3]](diffhunk://#diff-ee659a6ca157dc069b2bd1e958a707ff52fd76a93b00404c482a49284eb45641R143) [[4]](diffhunk://#diff-ee659a6ca157dc069b2bd1e958a707ff52fd76a93b00404c482a49284eb45641R201-R203)
* Updated constants and enums to support async output files, checks, and table types (e.g., `ASYNC_OUTPUT_CSV`, `SIMPLE_MODEL_RUN_ASYNC`, `ASNC_MODEL_RUN_CHECK`). [[1]](diffhunk://#diff-ee659a6ca157dc069b2bd1e958a707ff52fd76a93b00404c482a49284eb45641R30) [[2]](diffhunk://#diff-ee659a6ca157dc069b2bd1e958a707ff52fd76a93b00404c482a49284eb45641L116-R118) [[3]](diffhunk://#diff-ee659a6ca157dc069b2bd1e958a707ff52fd76a93b00404c482a49284eb45641R143) [[4]](diffhunk://#diff-ee659a6ca157dc069b2bd1e958a707ff52fd76a93b00404c482a49284eb45641R201-R203)
* Added `DEFAULT_ASYNC_API_NAME` constant for async endpoint naming.

**Column information refactoring:**

* Refactored `StoreAPI` to load column information using the new `ColumnsInformation` class instead of fetching schema directly from the output adapter, improving reliability and code clarity. [[1]](diffhunk://#diff-c07c157ec3f6da3baee1cd9cccd875b304da30507c10271d386b300511b6ca21R13) [[2]](diffhunk://#diff-c07c157ec3f6da3baee1cd9cccd875b304da30507c10271d386b300511b6ca21L80-R91)

**Miscellaneous:**

* Commented out calls to `delete()` in model runner to avoid premature model deletion during test stages. [[1]](diffhunk://#diff-82fa881a1c189eacfc2a0f2129d0b675d3345ccadd8c70960e7bedbc2c6b4d4fL184-R198) [[2]](diffhunk://#diff-82fa881a1c189eacfc2a0f2129d0b675d3345ccadd8c70960e7bedbc2c6b4d4fL624-R638) [[3]](diffhunk://#diff-82fa881a1c189eacfc2a0f2129d0b675d3345ccadd8c70960e7bedbc2c6b4d4fL634-R648) [[4]](diffhunk://#diff-82fa881a1c189eacfc2a0f2129d0b675d3345ccadd8c70960e7bedbc2c6b4d4fL643-R657)
* Minor import and code cleanups in several files. [[1]](diffhunk://#diff-8620dd3e2b759517ffaea20a9337f6405346f57cc5e3aa131618ae0ff4f7e775R1-R2) [[2]](diffhunk://#diff-8620dd3e2b759517ffaea20a9337f6405346f57cc5e3aa131618ae0ff4f7e775L20-R33)

These changes enhance the robustness and flexibility of the model testing workflow, especially for models exposing asynchronous endpoints.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e01ca766ffe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
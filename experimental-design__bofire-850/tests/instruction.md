# Issue

**Title:** Document the small data model packages

## Description

Continues the documentation migration (`tests/bofire/data_models/test_documentation.py`): every data model gets a docstring, and every own field a `Field(description=...)`, so the prose reaches `model_json_schema()`.

## Documented

- **`base`:** `BaseModel`.
- **`encodings`:** `OneHotEncoding.drop_first`.
- **`transforms`:** `Transform`, `DropDataTransform`, `ManipulateDataTransform`. They describe what the transforms do in a step of a stepwise strategy. The old `Attributes:` block of the manipulation transform named its fields wrongly.
- **`llm`:** the five LLM providers. The API key is read from the named environment variable when BoFire creates the client.
- **`descriptor_generators`:** `Fingerprints` (Morgan), `Fragments` (RDKit `fr_...` counts), `MordredDescriptors`.
- **`dataframes`:** rows, output values (validity, prediction, standard deviation, desirability), and the experiment and candidate tables.
- **`domain`:** `Domain` (`inputs`, `outputs`, `constraints`, `context`), `Constraints`, and the feature containers.

All `Attributes:` blocks in these packages are replaced by field descriptions. 61 allowlist entries are removed; after this PR and #843, only `strategies` and a few surrogates (pairwise, deterministic, empirical) remain.

## Changes on the way

- **Redundant redeclarations removed:** `ExperimentOutputValue.value` (identical to the base field) and `OpenAICompatibleLLMProvider.model` (identical to the base field).
- **Literal defaults** instead of `default_factory` in `Domain` and the containers, so they show up in the schema.
- **Breaking:** `DropDataTransform.to_be_removed_experiments`/`to_be_removed_candidates` are lists defaulting to `[]` instead of optional lists defaulting to `None` (both meant "drop nothing").
- **Breaking:** `Fingerprints.bond_radius` and `n_bits` must be positive.
- **Clearer messages:**
  - the data-frame check reported inconsistent output keys as "continuous input keys";
  - unknown `Fragments`/`MordredDescriptors` names are now listed, instead of the garbled "Not all provided … were not found".
- **Ratchet test:** it skips the classes pydantic generates for parametrized generics (e.g. `DataFrame[CandidateRow]`, `_BaseFeatures[...]`). They aren't declared in source and can't carry a docstring of their own; their generic carries the docs. They were on the allowlist with no way to ever leave it.

## Verification

- Full suite: 3247 passed; the only failures are `tests/bofire/strategies/doe/test_utils.py::test_n_zero_eigvals_*`, which also fail on `main`.
- Ruff clean; `ty` 154 diagnostics, as on `main`.

Overlap with #843: both edit the migration-status sentence in the CHANGELOG; whichever merges second combines the package lists.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce8cd50ceac2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
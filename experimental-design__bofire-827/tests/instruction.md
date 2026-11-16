# Issue

**Title:** Allow the last category as PositiveIndexKernel target_task_index

## Description

`PositiveIndexKernel.validate_target_task_index` rejects any `target_task_index >= num_categories - 1`, so with three categories only 0 and 1 are accepted and the last category can never be the one the covariance matrix is normalized against.

The botorch kernel this maps to (`botorch.models.kernels.positive_index.PositiveIndexKernel`, via `num_tasks=num_categories` in the mapper) checks `0 <= target_task_index < num_tasks`, so the data model was one stricter than the kernel it wraps. This loosens the bound to match: `>= num_categories` is rejected, `num_categories - 1` is accepted.

Tested with a new valid spec (`num_categories=3, target_task_index=2`) that fails validation on `main` and passes here, the existing invalid spec at `target_task_index=5` for five categories still raising, and `pytest tests/bofire/data_models tests/bofire/kernels` green. `ruff check`/`ruff format --check` clean on the touched files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ec41194c896`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
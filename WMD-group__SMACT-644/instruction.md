# Issue

**Title:** fix: make the structure prediction and solar oxides tutorials reproducible

## Description

Addresses #643, raised during the JOSS review (openjournals/joss-reviews#11015).

Both reproducibility failures the reviewer reported are fixed. In each case the underlying cause turned out to be slightly different from the initial diagnosis, so the fixes differ from what was suggested in the issue.

## `lambda.json` in the structure prediction and Doper examples

`CationMutator.from_json()` located pymatgen's lambda table by walking into pymatgen's install directory. That path is part of pymatgen's internal layout rather than its public API, and it moved: the data now lives under `pymatgen/core/structure_prediction/data/` instead of `pymatgen/analysis/structure_prediction/data/`, with the old module left as a re-export stub. The hard-coded lookup therefore raised `FileNotFoundError` on any current pymatgen. `Doper` reached the same failure through the same call, which is why `docs/examples/doper.ipynb` was affected too.

Rather than chase the file to its new location, the table is now bundled at `smact/data/lambda.json` and exposed as `DEFAULT_LAMBDA_JSON`. The vendored copy is byte-identical to pymatgen's (matching SHA-256), MIT licensed, and originally the data of Hautier et al. (2011). SMACT no longer imports pymatgen in `mutation.py` at all. A consequence worth noting for the review: the declared `pymatgen>=2024.2.20` floor is now accurate and needs no upper cap, since SMACT no longer depends on pymatgen's data layout.

## Multiprocessing in the solar oxides tutorial

The reviewer's report reproduces exactly: executing the notebook in a Jupyter kernel under the `spawn` start method fails with `AttributeError: Can't get attribute 'smact_filter' on <module '__main__'>`. The standard library pickles a notebook-defined function by reference, and that name does not exist in a freshly spawned worker. It passes on Linux today only because the default start method there is still `fork`.

Swapping in `multiprocess`, as the issue suggests, was not sufficient on its own. It ships the function's code but at default `dill` settings still resolves that function's globals by reference to `__main__`, so the notebook then fails with `NameError: name 'product' is not defined`. Three alternatives were tested; the tutorial now uses `pathos.multiprocessing.ProcessPool`, which needs no changes to `smact_filter`, no global `dill` settings, and is already a SMACT dependency used the same way in `smact/structure_prediction/database.py`.

## Verification

A clean Python 3.12 environment was built from a wheel produced by this branch, resolving to pymatgen 2026.5.4 — the reviewer's exact version. In that environment the old code path still raises their `FileNotFoundError` while the new one works, and `smact/data/lambda.json` is confirmed present inside the built wheel.

- Full test suite: 247 passed, 1 skipped on both pymatgen 2025.4.24 and 2026.8.13. The single skip is the Materials Project API test, which needs a key.
- `Doper(("Ti4+", "O2-"))` output is identical across both pymatgen versions.
- The structure prediction tutorial's stored outputs still reproduce exactly (0.00276 / 3.86 for Ba²⁺→Sr²⁺, and the rest).
- `docs/examples/doper.ipynb` executes end-to-end, including the `skipspecies` embedding path.
- The solar oxides tutorial runs end-to-end under both `spawn` and `fork`, giving identical results, including the two sequential pools.

## Changes

- `smact/data/lambda.json` — new, vendored verbatim from pymatgen.
- `smact/structure_prediction/mutation.py` — loads the bundled table via `DEFAULT_LAMBDA_JSON`; no longer imports pymatgen.
- `smact/tests/test_structure.py` — renames the misleading `test_pymatgen_mutator` fixture key to `default_mutator`, lets the three pymatgen cross-validation tests skip gracefully if pymatgen ever stops shipping its own copy, and adds `test_default_lambda_is_bundled_with_smact` as a packaging regression guard.
- `docs/tutorials/smact_generation_of_solar_oxides.ipynb` — uses `ProcessPool`, with a comment explaining why.
- `docs/tutorials/structure_prediction.ipynb` — corrects a comment that described the table as pymatgen's.

Notebook stored outputs are preserved and `nbstripout --verify` with the repo's arguments is clean. Ruff check, ruff format and codespell all pass.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

- **Bug Fixes**
  - Structure prediction now uses SMACT’s bundled lambda table by default, improving reliability when external pymatgen data is unavailable.
  - Default cation mutation and substitution workflows now load consistently across environments.

- **Documentation**
  - Updated structure prediction guidance to describe the bundled lambda table.
  - Improved the solar oxide generation tutorial’s parallel-processing instructions, including cross-platform notebook execution details and pool cleanup.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88f9a62ec0b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
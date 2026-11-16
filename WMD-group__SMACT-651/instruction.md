# Issue

**Title:** fix: make the documented install and the tutorials runnable as written

## Description

Found while checking that a JOSS reviewer following the README — or crispppp's own procedure from #643 (clean uv env on 3.12, `uv pip install smact`) — can actually run the examples and tutorials end to end.

Verified by building a wheel from `master`, installing it with `[optional]` into a clean Python 3.12 venv, and executing notebooks with `nbclient`. That env resolved **pymatgen 2026.5.4 — crispppp's exact version**.

## What was broken

**`structure_prediction.ipynb` could not be executed as written.** Two independent faults:

1. The API-key cell did `os.environ["MP_API_KEY"] = "<YOUR_MP_API_KEY>"`, which *overwrites a working key with the placeholder*. Every Materials Project call after it failed with `Invalid or old API key`. Both `SmactStructure.from_mp` (`structure.py:486`) and the notebook's own `get_MP_perovskite_data` already read `MP_API_KEY` **or** `PMG_MAPI_KEY`, so the cell was the only thing standing in the way. Now it only sets the placeholder when neither is configured.

2. Past that, `get_MP_perovskite_data` opens `MPRester(..., use_document_model=False)` — which returns plain dicts — and then reads `d.material_id` off them: `AttributeError: 'dict' object has no attribute 'material_id'`. Dicts are what the rest of the function wants, since `parse_mprest` indexes `data["structure"]`, so index the material id too.

**README overstated `smact[optional]`**, calling it "needed for full replication of examples and tutorials". It is not: `docs/examples/property_prediction.ipynb` needs `torch` and `aviary-models` from the `property_prediction` extra and dies on `import torch` without them. Confirmed empirically — it is the only example that fails under `[optional]`. The notebook's own Prerequisites section already names the right extra; only the README was wrong.

**`test_io.py` could hide a broken torch.** It used `pytest.importorskip("torch")`, which swallows `ImportError`. That matters because `torch` requires `nvidia-nccl-cu13` while `xgboost` — pulled in by `smact[ml]` inside the `optional` extra — requires `nvidia-nccl-cu12`, and **both ship the same file**, `nvidia/nccl/lib/libnccl.so.2`. Whichever installs last wins.

A fresh `uv sync --extra optional --extra property_prediction --dev` on my machine landed the cu12 copy, after which:

```
ImportError: .../torch/lib/libtorch_cuda.so: undefined symbol: ncclCommResume
```

and these 8 tests skipped silently while the suite still reported success (344 passed instead of 352 — green either way). Now the module skips only when torch is genuinely absent, so an installed-but-broken torch fails loudly. Verified both directions: errors in the broken env, `38 passed` in a healthy one.

## Notebook results so far

Reviewer env (wheel + `[optional]`, pymatgen 2026.5.4):

- **Examples: 10/11 pass.** Only `property_prediction.ipynb` fails, on the missing extra above. Notably `doper.ipynb` and the lambda-table path pass, confirming #644's fix holds on current pymatgen.
- **Tutorials:** `oxidation_states`, `element_embeddings_integration`, `filtering_icsd_oxidation_states` pass. `structure_prediction` failed for the two reasons fixed here.

## Not yet verified — please finish this

I ran out of session before completing the sweep. Still to confirm:

- `structure_prediction.ipynb` end to end **with these fixes applied** (it got past both faults; not yet run to completion).
- `metallicity_classification`, `smact_validity_of_GNoMe`, `crystal_space`, `smact_generation_of_solar_oxides` — all were still running or were killed by my teardown, so they have **no verdict**. `smact_generation_of_solar_oxides` alone ran 30+ minutes without finishing; it is heavy, not necessarily broken.
- `crystal_space_visualisation.ipynb` — failed for me with `FileNotFoundError: data/binary/df_binary_category.pkl`, but I ran it **before** `crystal_space.ipynb`, which produces that file. The toctree orders them correctly so a reader going top-to-bottom is fine; needs a re-run in the right order to confirm. Neither notebook states the dependency, which is worth a line of prose either way.

## Two things left for a maintainer decision

- **The nccl collision itself.** Only the test-masking is fixed here; the underlying conflict remains and can still produce a broken torch on a fresh sync. A `[tool.uv]` override could drop `nvidia-nccl-cu12`, but that would affect xgboost's GPU support, so it is your call rather than mine.
- **`docs/tutorials/test_db.db`** is written by running the structure prediction tutorial and is not gitignored, so a reviewer is left with an untracked file after following the docs.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

- **Documentation**
  - Clarified installation instructions for optional dependencies, including those required for band-gap prediction examples.
  - Added guidance for installing all dependencies needed to run the examples and tutorials.

- **Bug Fixes**
  - Updated the structure prediction tutorial to preserve existing API key settings and correctly process returned material data.
  - Improved test handling so genuine issues with installed machine-learning dependencies are reported instead of being silently skipped.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f276dd6b7ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
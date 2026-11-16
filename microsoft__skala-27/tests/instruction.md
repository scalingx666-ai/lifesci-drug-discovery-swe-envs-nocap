# Issue

**Title:** Add SHA-256 hash pinning for .fun file loading

## Description

## Summary

`torch.jit.load` deserializes arbitrary code via pickle, making it vulnerable to code execution if a `.fun` file is tampered with. This PR adds SHA-256 hash verification **before** calling `torch.jit.load`.

## Changes

- **`src/skala/functional/_hashes.py`** (new) — Pinned SHA-256 digests for `skala-1.0.fun` and `skala-1.0-cuda.fun` (from HuggingFace LFS OIDs).
- **`src/skala/functional/load.py`** — `TracedFunctional.load()` accepts a keyword-only `expected_hash` parameter. When provided, the file is read into memory, hashed with SHA-256, and verified before `torch.jit.load` is called. Raises `ValueError` on mismatch.
- **`src/skala/functional/__init__.py`** — `load_functional("skala")` looks up the pinned hash and passes it through. When `SKALA_LOCAL_MODEL_PATH` is used, hash verification is skipped with a logged warning.
- **`examples/cpp/cpp_integration/download_model.py`** — Now passes the expected hash when loading downloaded models.
- **`tests/test_hash_pinning.py`** (new) — 5 tests covering correct hash, wrong hash, opt-out (no hash), and file-path variants.

## Security model

| Load path | Hash verified? |
|---|---|
| `load_functional("skala")` via HuggingFace | ✅ Yes |
| `download_model.py` example | ✅ Yes |
| `TracedFunctional.load(path)` (no hash passed) | ⚠️ No (caller's responsibility) |
| `SKALA_LOCAL_MODEL_PATH` env var | ⚠️ No (user-trusted, warning logged) |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0af6c98653d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
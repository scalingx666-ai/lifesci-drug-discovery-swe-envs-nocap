# Issue

**Title:** Fix RAG embedding download: use snapshot_download instead of SentenceTransformer.save()

## Description

FOR CONTRIBUTOR:
* [x] This PR updates an existing tool or tool collection

Replaces `SentenceTransformer.save()` with `huggingface_hub.snapshot_download()` in `download_embeddings.py`. ST 5.4.1's `save()` rewrites `modules.json` with class paths (`sentence_transformers.base.*`) that don't exist in ST 5.3.0 (the container version), causing `ModuleNotFoundError`. `snapshot_download` preserves HF Hub files as-is, keeping stable `sentence_transformers.models.*` paths.

Also adds PEP 723 inline metadata so `uv run` resolves deps without `--with sentence-transformers` (shrinks from 50+ packages to just `huggingface_hub`).

**Server action required:** existing model dirs on sn09 must be removed and re-downloaded with the updated script.

ref:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52a7de624e5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
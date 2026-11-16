# Issue

**Title:** evo2 SAE recipe: streaming extract + train (7B layer-26)

## Description

## What

Adds the **Evo2 SAE recipe** under `recipes/evo2/` — the runnable pipeline that turns Evo2 activations into a trained SAE:

```
chunk FASTA  →  stream-extract (extract.py)  →  train (train.py)
```

`scripts/7b.sh` runs all three and reproduces our **layer-26 7B (`normalize_input`)** run.

## Contents
- **`extract.py`** — streaming activation extractor: reuses `predict_evo2` for the Megatron forward but writes layer-L activations **directly to a parquet `ActivationStore`** (no intermediate `.pt`). Model-agnostic (1B/7B/40B).
- **`train.py`** — trains a TopK/ReLU SAE from the activation cache. Never loads the model (reads only the cache; `--model-path`/`--layer` validate metadata only).
- **`chunk_fasta.py`**, **`7b.sh`** (orchestrator), **`pyproject.toml`**.

_(README/usage docs deferred to a follow-up, once the pipeline is merged and exercised end-to-end.)_

## Opt-in training fixes (from the merged `sae` PR #1619)
All default to the **previous behavior** — omit them to reproduce a baseline run exactly:

| flag | effect |
|---|---|
| `--aggregate-loss` | batch-level FVU + AuxK loss vs the per-token ratio |
| `--dead-count-global` | count dead-latent inactivity in total tokens (× world_size) under DDP |
| `--mix-shards N` | shuffle + blend N shards/batch (replaces the old `--shards-per-buffer`) |
| `--presample-shards N` | spread the pre-bias-init sample across N shards |

The DDP per-epoch batch cap is computed from each rank's assigned shards + `all_reduce(MIN)`, so it stays correct when `mix_shards>1` shuffles the shard list.

## Model format
Assumes a local **Evo2 MBridge checkpoint** (`--ckpt-dir`, loaded by `predict_evo2`). Getting it — **NGC pull** or nemo2→MBridge convert — is a documented **prerequisite**, not recipe code (no Savanna conversion baked in). (Contrast CodonFM, whose Encodon model is an HF/TransformerEngine `.safetensors` — different model family + runtime, hence the different extractor.)

## Duplicate code & planned consolidation
This recipe deliberately **mirrors the existing CodonFM recipe** rather than deduplicating now:

- **`train.py` is essentially the same file as `codonfm/scripts/train.py`** — byte-identical before the Evo2 skin + the four opt-in flags. Both are thin wrappers over the shared `sae.training.Trainer`.
- **`extract.py` shares its skeleton with `codonfm/scripts/extract.py`** — both run a model forward and stream into a `sae.ActivationStore`, including a near-identical **per-rank shard merge** (`_merge_temp_stores` ≈ CodonFM's `_merge_rank_stores`). Only the model-loading differs (Evo2 via Megatron `predict_evo2` vs CodonFM's HF/TE loader).

Consolidating either means factoring the shared **train-CLI** and the **parquet-shard merge** into the `sae` package **and migrating CodonFM onto them** — a cross-recipe refactor touching another recipe. To keep this PR single-concern (and avoid re-tangling, which this PR stack exists to undo), that dedup is a **planned follow-up** (alongside the duplicated-dashboard-component dedup), not part of this PR.

## Tests
Following the existing recipes' convention (CodonFM, ESM2 ship **no recipe-level tests**), the tested logic lives in the **`sae` package** — e.g. the opt-in flags' config round-trip is covered by `sae/tests/test_topk.py` (#1619). This recipe is a thin driver over that tested package. The streaming `extract.py` and the DDP shard-count path need a multi-GPU run to verify.

## Supersedes
Replaces #1579 (recipe) and #1583 (tangled extract+recipe), which also smuggled the now-merged `evo2_megatron` (#1618) and `sae` (#1619) changes. Closed both in favor of this clean, single-concern recipe carved off `main`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e5a86545d93`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
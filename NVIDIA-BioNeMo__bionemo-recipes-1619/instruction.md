# Issue

**Title:** sae: config-gated dead-latent/FVU training fixes + inter-shard shuffle & pre-bias init shard sampling

## Description

## Why

Training TopK SAEs on Evo2 activations hit a severe **dead-latent** problem (a large fraction of features never fired, wasting capacity). `normalize_input` (already merged) fixed most of it; this PR adds the remaining **training-dynamics fixes we found necessary for Evo2 SAE training**.

**Every change defaults to the previous behavior and is opt-in** — so you can reproduce or continue prior training runs **exactly as before**, and enable each fix only when you want it. The training recipe opts in; both `topk` options serialize in the checkpoint config so a reloaded SAE keeps its behavior.

## Changes — default = previous behavior, opt in per flag

**1. Dead-latent inactivity counted in *total* tokens** — `dead_count_global` (default `False` = previous per-rank count)
The auxk revival fires once a latent has been inactive for `dead_tokens_threshold` (10M) tokens, but the counter advanced by *this rank's* micro-batch — so under DDP it ran `world_size`× too slow and revival kicked in `world_size`× too late (≈80M effective tokens on 8 GPUs). Opt in with `dead_count_global=True` to count total tokens (× world_size); the `all_reduce(MIN)` still means "fired on any rank ⇒ reset."

**2. Aggregate FVU + auxk loss** — `aggregate_loss` (bool, default `False` = previous per-token)
The per-token loss ratio `mean_t(mse_t / var_t)` down-weights rare high-variance tokens, starving the latents that specialize on them (notably Evo2's heavy-tailed **sink tokens**) → they die. Opt in with `aggregate_loss=True` for a batch-level ratio (which also matches the reported `var_exp` metric). This single bool also fixes the **auxk residual** end-to-end: `False` keeps the previous `x - recon + pre_bias`; `True` uses the corrected `x - recon` (the true error, not `pre_bias`-dominated).

**3. Shuffle + blend shards** — `mix_shards` (int, default `1` = previous)
Shards are written in corpus order (all prokaryota, then all eukaryota). A contiguous per-rank slice trains a rank on one kingdom then switches mid-epoch → a visible **FVU cliff**. `mix_shards=1` (default) = previous behavior (one shard at a time, contiguous slice). Set `mix_shards=N>1` to **globally shuffle the shard list** before the per-rank split (so each rank gets a cross-section) **and** buffer/blend N shards per batch (≈N shards of peak RAM).

**4. Spread the pre-bias-init sample** — `sample(num_shards=…)` (default `1` = previous single shard)
`pre_bias` is initialized to the geometric median of a sample of activations (so the SAE starts centered). A single-shard sample biases it toward whatever is first in corpus order (one kingdom) → mis-centered init → more dead latents. Set `num_shards>1` to draw the sample across that many random shards spanning the store (≈one shard of peak RAM — each sub-sampled then freed).

## How to opt in (what the Evo2 recipe sets)
```python
TopKSAE(..., aggregate_loss=True, dead_count_global=True)
store.get_streaming_dataloader(..., mix_shards=8)             # shuffle + blend 8 shards
pre_bias0 = geometric_median(store.sample(n, num_shards=8))   # sample across 8 shards
```
The training recipe (separate PR) exposes these as CLI flags (`--aggregate-loss`, `--dead-count-global`, `--mix-shards`, `--presample-shards`).

## Opt-out summary

| behavior | knob | default | opt in |
|---|---|---|---|
| global dead-token count | `dead_count_global` (bool) | `False` | `True` |
| aggregate FVU + auxk loss | `aggregate_loss` (bool) | `False` | `True` |
| shard shuffle + blending | `mix_shards` (int) | `1` | `>1` |
| spread pre-init sample | `sample(num_shards=)` | `1` | `>1` |

## Tests — `sae/tests/test_topk.py` (CPU, no GPU)
global-vs-local dead-token counting, the aggregate-FVU formula (`mse.mean()/var.mean()`), and that the opted-in flags round-trip through `_get_config()`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78e9fa0dc20b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
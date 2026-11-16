# Issue

**Title:** ci: GPU matrix lane for interpretability SAE recipes (merge-first, presence-guarded)

## Description

## What
A GPU CI **matrix lane** for the SAE interpretability recipes under `interpretability/sparse_autoencoders/recipes/*`. Modeled on the repo-wide `unit-tests-recipes.yml`: a cheap ubuntu `changed-dirs` job discovers which interp recipes to test and emits a matrix; a per-recipe `unit-tests` job runs each on an L4 (its own `.ci_build.sh` + `pytest tests/`).

## Which recipes are eligible
Any interp recipe that has its own **`.ci_build.sh`**. Today that's **evo2**. `codonfm`/`esm2` have no `.ci_build.sh`/tests yet, so they're **skipped until they add them** — at which point they auto-join this lane, no workflow change needed. (This is also the **presence guard**: before the evo2 SAE recipe lands, #1622, nothing is eligible → the whole lane is a green no-op, so it can merge first.)

## What runs, when
| What the PR changes | Which recipes run |
|---|---|
| a recipe's own dir — `…/recipes/<X>/**` | just **`<X>`** |
| the shared `sae` lib — `…/sparse_autoencoders/sae/**` | **all** eligible recipes (they all depend on sae) |
| this workflow file | **all** eligible recipes |
| **nightly** `schedule` @ 09:00 UTC | **all** eligible recipes |
| anything else (other recipes' dirs, docs, …) | **none** — empty matrix, green no-op |

- **Megatron *build* is per-recipe — only evo2 builds it.** Each recipe's own `.ci_build.sh` owns its build: **evo2** compiles/installs the mbridge `bionemo.evo2` (megatron) stack; a future HF-native **esm2** or custom **codonfm** builds its own thing, *no megatron*. So a codonfm/esm2 change never pays for the Evo2 megatron build — it runs only on an evo2 change (or an `sae`/nightly run, which tests every consumer, evo2 included).
- **Container *image* is currently shared.** All matrix entries use one base image (`svcbionemo023/…pytorch26.04-py3-squashed`, dockerhub-cached → cheap after first pull) — the megatron-capable base evo2 needs. A future HF-native recipe *runs in* that base but doesn't build megatron on top. If a recipe later wants a lighter image, the matrix can carry a **per-recipe `image`** (like the repo-wide lane's `matrix.recipe.image`) — not needed while evo2 is the only active recipe. Net: **shared base image, per-recipe (megatron-or-not) build.**
- Each eligible recipe runs on the **L4** against its **CI-sized model** (evo2 = the auto-built **1B**). The **7B/L26** path is manual (`EVO2_CKPT_DIR`), never in CI.
- Not covered: the React dashboard frontend (no JS build step) and offline `extract`/`train` scripts (no unit tests).

## Validation
Proven end-to-end on a real L4 via the #1670 test PR:
**https://github.com/NVIDIA-BioNeMo/bionemo-recipes/actions/runs/28535969801** — the L4 built via `.ci_build.sh` and ran the evo2 recipe suite green (**54 recipe tests passed**). The `changed-dirs` matrix logic was verified locally across 8 scenarios (per-recipe / sae-change / nightly / pre-#1622-empty). Trigger = a maintainer commenting `/ok to test <sha>`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `04d65c98d881`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
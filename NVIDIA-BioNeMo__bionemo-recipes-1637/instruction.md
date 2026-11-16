# Issue

**Title:** evo2 SAE serve: FastAPI server + CLI (on the engine)

## Description

## Summary
FastAPI **server + CLI** over the Evo2SAE engine (#1622). Thin wrappers — all model work lives in `core.py` — plus the input validation, resource governance, and recovery needed for a shared backend (runs behind NVIDIA SSO on Brev, reachable by many users). API routes live under **`/api`**, and the server can mount a prebuilt front-end at `/`, so the dashboard (#1623) and the API can be served from **one origin / one container**.

**Rebased onto the single-engine #1622** (one inference engine serves both encode and generate; new top-level layout `interpretability/sparse_autoencoders/…`).

## Contents (new layout)
- `…/src/evo2_sae/server.py` — `/api/health`, `/api/features`, `/api/annotate`, `/api/generate` (+ optional static-frontend mount at `/`)
- `…/src/evo2_sae/cli.py` — `serve` / `encode` / `batch` / `generate`
- `…/scripts/launch_inference.sh`; CPU contract tests `tests/test_cli.py`, `tests/test_server.py` + the shared `FakeEngine` appended to #1622's `tests/conftest.py`

## Shared logic (CLI ⇄ server live in `core`)
- **`core.annotate(engine, …)`** — clean → resolve-tag → encode → tag-len, behind both CLI `encode` and server `/api/annotate`.
- **`core.parse_clamp_spec(spec)`** — one parser for clamps as CLI `"ID[:STRENGTH]"` strings or server `FeatureClamp` JSON; fed in front of #1622's `_sanitize_steering` so both surfaces validate identically.

## Single-origin serving (`/api` + optional static mount)
- API routes are grouped under **`/api`** (one `APIRouter` + `include_router`).
- `build_app(engine, static_dir=None)` mounts a prebuilt front-end at `/` via `StaticFiles(html=True)` when `static_dir` (or the `DASHBOARD_DIST` env) points at a real directory; otherwise the server is **API-only** and `/` 404s (never crashes). The mount is generic — it serves whatever dir it's pointed at and knows nothing about the dashboard; #1623 supplies the dir + the Docker build that produces it.
- This is what lets a single container serve UI + API on one port. Dev hits the same `/api/*` paths (the Vite proxy forwards `/api` without rewriting), so there's no dev/prod path drift.

## Reliability & governance
- **`/api/health` 503 until ready** so readiness probes don't route to a still-loading pod; a startup load failure is caught and leaves the engine not-ready (503) rather than crashing.
- **Length limits** — `/api/annotate` and `/api/generate` reject input longer than `max_seq_len` (**413**) instead of silently truncating (which would misalign the per-base `activations`/`bases` the viz plots). Generation length is otherwise auto-capped to the remaining context (no fixed token cap).
- **Pick-id validation** — `/api/annotate` `mode=pick` range-checks user-supplied `feature_ids` → **400** (an out-of-range id would otherwise 500 on `IndexError`, a negative one would silently return the wrong feature).
- **Steering sanitation** — out-of-range ids, extreme/non-finite strengths, `temperature<=0`, negative `top_k` are all rejected/coerced before the GPU (`_sanitize_steering`).
- **CUDA-wedge recovery** — a device-side assert poisons the process's CUDA context (unrecoverable in-process). Not client-inducible (sanitation covers the reachable triggers — purely defensive), but if it happens `generate()` flips the engine not-ready (→ 503) and, when `EXIT_ON_CUDA_WEDGE=1` (set by `serve`), exits the worker so any restart-on-exit supervisor respawns it — host-independent recovery.
- **Signal-safe serve** — `launch_inference.sh serve` runs the worker in the background, forwards `SIGTERM`/`SIGINT` (uvicorn graceful shutdown) before respawning, with a retry cap + backoff, so `docker stop`/k8s shuts down cleanly instead of orphaning the worker.
- **Request body-size limit** (`MAX_BODY_BYTES`, default 16 MiB) → 413 — advisory (trusts `Content-Length`).
- **Bounded concurrency** — Starlette's sync-endpoint threadpool capped (`MAX_CONCURRENCY`, default 8); the engine lock already serializes the single GPU.

## Architectural decisions
- **Two layers: engine vs. surface.** All model work stays in `core.Evo2SAE` (#1622); `server.py`/`cli.py` are thin and share `core.annotate` + `core.parse_clamp_spec`, so the HTTP API and the CLI can't drift and there's one validated path.
- **FastAPI, not raw/Flask.** We get pydantic structural validation + an async threadpool we can bound (`MAX_CONCURRENCY`) for almost no code; the domain validation that matters (`_sanitize_steering`, pick-id range) is manual either way. Raw Python would hand-roll routing/validation/concurrency; Flask would add the threadpool governance by hand.
- **No app-level auth.** Deployed behind NVIDIA SSO on Brev; auth is the proxy's job, not duplicated here (CORS removed too — calls are same-origin).
- **Single GPU, serialized.** The engine lock + bounded threadpool match one GPU; data-parallel replicas behind a balancer are a deferred follow-up (touches no engine code).
- **`/api` prefix + generic static mount** (above) so one origin/container can serve both UI and API.

## How to run
Run **inside the evo2_megatron venv** (provides `bionemo.evo2` + megatron); in the Docker image it's already active. Full dashboard run modes are in #1623's `feature_explorer/README.md`.
```bash
export EVO2_CKPT_DIR=<mbridge>  SAE_CKPT_PATH=<sae.pt>
export FEATURE_ANNOTATIONS=<feature_metadata.parquet>  EMBEDDING_LAYER=26
scripts/launch_inference.sh serve                                    # API on :8001 (+ UI at / if DASHBOARD_DIST set)
scripts/launch_inference.sh encode   --sequence ATGC...              # one sequence -> top features (JSON)
scripts/launch_inference.sh batch    --fasta in.fa --out out.parquet # many -> parquet
scripts/launch_inference.sh generate --prompt ATGC... --clamp 29244:300  # steered generation
```
Tunables (env): `MAX_BODY_BYTES`, `MAX_CONCURRENCY`, `MAX_SEQ_LEN`, `PORT`, `EXIT_ON_CUDA_WEDGE`, `DASHBOARD_DIST`.

## Tests
No dedicated CI lane (deferred — ). Run them via the recipe's build script:
```bash
cd interpretability/sparse_autoencoders/recipes/evo2
bash .ci_build.sh && source .ci_test_env.sh
pytest tests/
```
- **CPU (no model):** `test_cli.py` + `test_server.py` (FastAPI `TestClient` + `FakeEngine`: response shapes, 400/413/503, pick out-of-range → 400, `/api/generate` too-long → 413, body-size, k-bounds, clamp validation, **static-frontend mount: SPA at `/`, asset served, API reachable under `/api`, unknown `/api/*` → 404, API-only when no frontend**), plus #1622's `test_core.py` + `test_steering.py` sanitize guards.
- **GPU:** `test_steering.py` — encode, in-distribution generation, steering changes the continuation, batched/empty encode, max-clamp finite, **highlight↔steer interleaving** (single-engine state-bleed check). Gated by `@pytest.mark.skipif(not torch.cuda.is_available())` — runs on a GPU box, skips otherwise. Validated on the 1B; the single-engine backend also serves the **7B at layer 26** live.

## Deferred follow-up
Multi-GPU **data-parallel replicas** (one worker per GPU behind a `least_conn` balancer) for concurrent throughput — touches no engine code; left until concurrency is an observed need.

**Stacked on #1622.** The dashboard (#1623) builds on this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c31d4e9ac7fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
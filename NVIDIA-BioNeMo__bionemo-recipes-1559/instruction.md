# Issue

**Title:** Jwilber/update conv schedule

## Description

Update schedule to run less frequent, and update esm2 jobs:

- `.github/workflows/scdl-performance-tests.yml` — scdl now runs weekly on Fridays 2pm PST (0 22 * * 5) instead of daily.

- `.github/workflows/convergence-tests.yml` — single cron 0 8 * * 0 (Sun 00:00 PST = Sat night midnight), a new gate-biweekly job that skips odd ISO weeks, and the matrix runs all three configs (esm2_650m, esm2_15b, codonfm_ptl_te) on every scheduled run.

- `ci/lepton/.../esm2_native_te_15b.yaml` — num_train_steps: 20_000 → 500.

- `ci/lepton/.../esm2_native_te_650m.yaml` — added top-level fp8_recipe/fp8_format, two new FP8 products (bshd+fp8, thd+fp8) mirroring the 15b config, and extended run_script to pass both fp8 params.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `afd48cd3f264`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
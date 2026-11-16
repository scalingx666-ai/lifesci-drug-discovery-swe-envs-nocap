# Issue

**Title:** fix(workflow): read potcar_root from hpc.job_defaults (fixes missing POTCAR → VASP fail)

## Description

## Bug

VASP jobs submitted by the workflow engine died in ~6 seconds with:
> `forrtl: severe (29): file not found, unit 10, file .../POTCAR`

The job ran (read POSCAR correctly) but no POTCAR was in the work dir.

## Root cause

`_submit_one` read POTCAR settings only from the hpc **root**:
```python
potcar_root = config.get("hpc", {}).get("potcar_root", "")   # often ""
```
But when `potcar_root` comes from `default_job_params`, the scanner lands it in `config["hpc"]["job_defaults"]` and only promotes it to the hpc root **when a per-session `cluster_config` supplies it** (`scanner.py:392`). For a workflow with an empty `cluster_configs` (the common case), the root value is `""`, so `if potcar_root:` was false and **POTCAR generation was silently skipped** — VASP then failed on the missing POTCAR.

## Fix

`_resolve_potcar_settings(config)` reads `hpc.potcar_root` first, then falls back to `hpc.job_defaults.potcar_root` (same for `potcar_functional`). When neither is present it logs a warning instead of silently producing a doomed job.

## Test

`test_potcar_root_resolution.py` — job_defaults-only, hpc-root, precedence, and absent (defaults). **4 passed.**

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `418e698523c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
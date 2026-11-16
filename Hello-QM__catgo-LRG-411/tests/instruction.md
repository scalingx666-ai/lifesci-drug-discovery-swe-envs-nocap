# Issue

**Title:** fix(workflow): JobScriptParams accepts potcar_root (fixes dropped POTCAR config)

## Description

## Bug

VASP workflow jobs died with `severe (29): file not found ... POTCAR`. A `potcar_root` set in the run config's `default_job_params` never reached the submitter.

## Root cause

`default_job_params` is typed as `JobScriptParams`, which only declared `nodes/ntasks/cpus_per_task/walltime/partition/memory/account` — **no `potcar_root`**. So Pydantic silently dropped `potcar_root`/`potcar_functional` on every `/run`. The scanner then had no potcar_root to copy into `hpc.job_defaults`, the submitter's `_resolve_potcar_settings` returned `""`, and POTCAR generation was skipped → VASP failed.

(Pairs with the companion fix where the submitter reads potcar_root from `hpc.job_defaults`, not just hpc-root.)

## Fix

Add `potcar_root: Optional[str] = None` and `potcar_functional: Optional[str] = None` to `JobScriptParams`. Purely **additive + backward compatible** — no existing field or default changed; frontend submissions that don't set potcar_root here are unaffected.

## Test

`test_runconfig_potcar_root.py` — potcar_root survives both `JobScriptParams` and `WorkflowRunConfig` validation; defaults to None. **3 passed.**

## Verified live

With this fix, the run config's `potcar_root` survives `/run`, the submitter generates a 228 KB POTCAR remotely, and a real VASP geo_opt job ran on Expanse (no longer dies in 6 s).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `418e698523c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
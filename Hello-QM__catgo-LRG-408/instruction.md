# Issue

**Title:** fix(workflow): reset clears stale hpc_job_id + work_dir (re-run submits fresh)

## Description

## Bug

After resetting a workflow, each task kept its **old `hpc_job_id`**. On the next run the engine polled that (now finished/cancelled) job, saw it was gone, and marked the task **FAILED** — the whole workflow failed without ever submitting a new calculation. `reset_workflow`'s docstring even said *"Does NOT clear work_dir/hpc_job_id."*

Found live: a reset ORR workflow kept `hpc_job_id=51381735` (a cancelled job); every re-run immediately failed.

## Fix

`reset_workflow` (`server/catgo/workflow/engine/lifecycle.py`) now clears `hpc_job_id` and `work_dir` when resetting tasks to WAITING, so a re-run submits fresh jobs and re-resolves the work dir against the current config.

## Test

`test_reset_clears_job.py`: a FAILED task with a stale `hpc_job_id`/`work_dir` is cleared by `reset_workflow`. **Passes.** Verified live: after the fix, reset reported no steps holding a stale job id.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `418e698523c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
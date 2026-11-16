# Issue

**Title:** fix(hpc): support conn.run(input=) on subprocess SSH + local runners

## Description

## Symptom

Running a workflow on HPC (Expanse, system-ssh/ControlMaster connection) — a Geometry Optimization step goes **FAILED** with:

> Submit failed: SubprocessSSHRunner.run() got an unexpected keyword argument 'input'

## Root cause

The submitter uploads (possibly user-edited) **preview** input files to the cluster via `conn.run("cat > {file}", input=content)` (`submitter.py:256`). The asyncssh connection backend accepts `input=` (pipes to stdin), but the two subprocess backends — `SubprocessSSHRunner` (system `ssh` + ControlMaster) and `LocalCommandRunner` — did **not** define the kwarg, so any task whose connection used them crashed the moment it tried to upload reviewed files.

## Fix

Add `input: str | None = None` to `SubprocessSSHRunner.run` / `run_raw` and `LocalCommandRunner.run`. When provided, open `stdin=PIPE` and feed it via `communicate(input.encode())` — matching the asyncssh `conn.run(..., input=...)` interface the caller expects.

## Verification

- `test_local_connection_input.py`: `LocalCommandRunner.run("cat > f", input=...)` writes the file end-to-end (real subprocess); the no-input path still works; both runners expose the `input` kwarg. **4 passed.**
- Note: pytest-asyncio is not installed in this repo (the `asyncio_mode` ini is ignored and bare `async def test_` are silent no-ops), so the new tests drive coroutines via `asyncio.run()` and actually execute.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27f7f553db54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
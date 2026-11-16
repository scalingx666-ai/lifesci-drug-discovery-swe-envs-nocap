# Issue

**Title:** Friendly errors instead of tracebacks for serve/info/close

## Description

Replaces three tracebacks with the usual red CLI messages.

## Changes

### `ersilia serve` on a model that is not fetched
Declining the fetch prompt raised a bare `Exception` and printed a traceback. It now raises the existing (previously unused) `ModelNotAvailableLocallyError`, and `serve` shows:

```
✖  Model eos5j3l is not available locally, so it cannot be served.
▪  Fetch it first by running: ersilia fetch eos5j3l
```
and exits with code 1.

### `ersilia info` / `ersilia close` / `ersilia run` with no model served
A failed `serve` saves a session file with store settings but no `model_id`, so the next `info`, `close` or `run` crashed with `KeyError: 'model_id'`. The single-value `Session` accessors (`current_model_id`, `current_service_class`, `current_identifier`, `current_output_source`, `current_local_cache_status`, `tracking_status`) now return `None` for a missing key, as their docstrings already promise. `current_store_status` returns `None` when the store keys are missing. The commands then show their existing messages ("No model is currently served." / "No model was served" / "No model seems to be served. Please run 'ersilia serve ...' before.").

## Testing
- Reproduced the `KeyError` on `master` (failed `serve`, then `info`); it no longer occurs with this branch.
- After a failed `serve`, `ersilia info`, `ersilia close` and `ersilia run` print their normal messages instead of tracebacks.
- `pytest test/cli test/test_process_cleanup.py`: 21 passed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b3f34b509732`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
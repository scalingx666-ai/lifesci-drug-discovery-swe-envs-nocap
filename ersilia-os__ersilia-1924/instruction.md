# Issue

**Title:** fix: kill orphaned model servers and stream large run output to disk

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [ ] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description**
- ersilia close only killed the ersilia_model_serve wrapper PID, orphaning the
  run_uvicorn.py child. Add kill_process_tree (SIGTERM, then SIGKILL) and use it
  in all kill sites. Always shut down the fetch-time example server, even when
  the example run fails.
- StandardCSVRunApi.post kept all results in memory and made several full
  copies before writing, which OOMs on large runs with wide outputs. Write each
  batch to csv/tsv/h5 as it arrives

**Changes to be made**
- `ersilia/utils/session.py`: new `kill_process_tree(pid)`. It sends SIGTERM to the process and all its descendants, waits, then SIGKILLs any survivors and waits for them to exit.
- Use it at every kill site: `_FastApiService.close` (`serve/services.py`), `AutoService._kill_pids` (`serve/autoservice.py`) and `purge_session_processes` (`utils/session.py`).
- `hub/fetch/fetch.py`: `_standard_csv_example` wraps the example run in `try/finally`, so the model is always closed.
- `serve/standard_api.py`: `post` streams each batch to disk as it arrives. `_fetch_result` takes an optional `on_batch` callback.
- `io/output.py`: new `GenericOutputAdapter.write_chunk`. `DataFrame.write` supports `append` for csv/tsv/h5.
- `utils/hdf5.py`: `Hdf5Data.save` creates resizable datasets and supports appending.

**Status**
- Process cleanup: after `ersilia serve eos1soi` + `ersilia close`, no wrapper or uvicorn processes remain. New tests in `test/test_process_cleanup.py` (9). They fail on the old kill code and pass with the fix.
- Streaming output: old and new code produce identical output on eos3l5f (768 floats) and eos4k4f (strings), 2,500 molecules, csv and h5. CSVs match byte for byte; every HDF5 dataset matches in shape, dtype and values. On 20k molecules × 768 columns, peak memory of the `ersilia run` process went from 3,069 MB to 405 MB. New tests in `test/test_streaming_output.py` (6).
- `.h5` outputs are ~1.5–7% larger, because resizable datasets use chunked storage.
-

Is this pull request related to any open issue? If yes, replace issueID below with the issue ID

Related to #1921 #1844

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `481f746d7b7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
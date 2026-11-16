# Issue

**Title:** Performance improvements for run/serve/close

## Description

Small, low-risk performance changes to `ersilia run` / `serve` / `close`, one commit per step.

**Overall:** about 0.8 s less fixed overhead on every `run` and `close` (steps 1, 3, 5), HDF5 output written 3× faster, and runs can no longer hang forever on a stuck model server.

## Changes

### 1. Build each service backend once in `AutoService`
`AutoService.__init__` constructed every candidate service class twice: once to call `is_available()`, then again to keep as `self.service`. Constructors are expensive; for example, `PulledDockerImageService` runs `docker ps`, `docker context show/inspect` and `docker.from_env()`. Each class is now built once and reused.
- Explicit service class (every `run`, `close` and repeat `serve`): build → check → reuse.
- Auto-detection (first `serve`): one ordered candidate loop. The order, the `service_class.txt` write and the `DummyService` fallback are unchanged.

**Measured** (`AutoService("eos42ez", service_class="pulled_docker")`, median of 5, macOS with Docker): **0.70 s → 0.53 s** per construction. This cost is paid on every `ersilia run` and `ersilia close`.

### 2. One HTTP session for run batches, with timeouts
Batches were sent with a bare `requests.post` with no timeout: a new connection per batch, and a stalled model server hung `ersilia run` forever.
- All batches go through one `requests.Session` (connection reuse; also the base for concurrent batches later).
- Timeouts: **connect 60 s, read 10 h** (`RUN_CONNECT_TIMEOUT` / `RUN_READ_TIMEOUT` in `default.py`). The read timeout is the longest the server may stay silent on one batch, not a limit on total run time.
- **Timeouts and connection errors now fail right away** with a clear error. Previously the batch would be split in half and retried down to single molecules, repeating the wait for every half. For a dead server, that also silently wrote empty outputs. HTTP errors such as 500 still split the batch to isolate bad inputs, as before.

**Measured** (local HTTP server, 1000 batches of 100): 0.89 → 0.64 ms per batch. That's small, about 2.5 s saved per 1M molecules. The main value here is the timeout and the fail-fast.

### 3. Set up Redis only when serving
`AutoService` created `SetupRedis` in its constructor, which runs `docker info`, `docker context show/inspect`, `docker.from_env()` and a ping, on every `run` and `close`. Only `serve()` uses it, so it is now created there. `serve` behaves the same: with `--enable-cache`, Redis still starts; with the cache off, the Redis container is still removed.

**Measured** (`AutoService("eos42ez", service_class="pulled_docker")` with the default `cache=True` that `run`/`close` use, median of 5): **0.51 s → 0.26 s**.

**End to end:** `ersilia serve eos42ez` → `run` ×2 → `close` all succeed on this branch, and both runs produce identical output.

### 4. Write each run batch in one pass
Streaming runs turned every batch into per-row dicts, rebuilt them as rows with a cast for every cell, then formatted every cell again before `csv.writer`, which already does that formatting. `GenericOutputAdapter.write_batch` now builds rows straight from the merged results and converts float outputs as one numpy matrix. HDF5 batches pass that matrix to `Hdf5Data` directly.

**Measured** (100 rows × 2048 float columns per batch):
- **HDF5: 32 → 10 ms/batch**
- **CSV: 166 → 150 ms/batch.** Most of what remains is converting the floats to text (~84 ms), which is left as is so the file format stays the same.
- 3-column models: unchanged (<1 ms).

**Output is identical:** a comparison against `master` covering float, int, string and mixed columns; CSV, TSV and HDF5; empty rows and cells; odd values (`"0.10"`, `" 2.5 "`, `True`, `nan`, `inf`); quoted SMILES; and appends across batches gave the same CSV/TSV bytes and HDF5 datasets.

### 5. Import heavy libraries only where they are used
Importing `ersilia.core.model`, which `serve`, `run`, `close`, `info` and others do, loaded pandas, h5py, boto3, redis and the whole fetch/delete module chain at startup, although a normal run needs none of them. Those imports now happen at their use sites:
- `core/model.py`: `ModelFetcher`, `RunTracker`, `Hdf5DataLoader`, `InferenceStoreApi`, pandas
- `serve/standard_api.py`: pandas. The empty placeholder cache table built per batch is now `None`, which `_merge_cache_and_api` already handles.
- `serve/autoservice.py`: `SetupRedis`
- `io/output.py`: `Hdf5Data` / `Hdf5DataStacker`
- `store/isaura.py`: pandas

What still loads (requests, numpy, docker, psutil) is used when running a model.

**Measured:**
- `import ersilia.core.model`: **0.70 s → 0.27 s**
- `ersilia close` / `ersilia info` with nothing served: **0.78 s → 0.35 s** (median of 7)

**End to end:** `serve eos42ez`, `run` to CSV and to HDF5, `info` and `close` all succeed, and the CSV is byte-identical to the earlier run.

## Testing
- `ruff check` / `ruff format --check` pass
- New `test/test_run_http.py` (local HTTP server): connection reuse, a dead server fails fast, a hung server fails after one request, and HTTP 500 still splits the batch
- `pytest test --ignore=test/fields`: 83 passed, 2 errors, the same as on `master`. The 2 errors are in the URL-search benchmark test and fail on `master` too. `test/fields` needs `pyairtable`, which isn't installed in this environment.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b2df5b0e561`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
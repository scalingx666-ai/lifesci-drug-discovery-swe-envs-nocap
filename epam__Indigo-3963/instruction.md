# Issue

**Title:** Fix #635: Bingo DB read_only should request a shared, not exclusive, lock

## Description

## Summary

.

`BaseIndex::load()` requested an exclusive `flock()` on the database directory's lock file *before* parsing the `options` string, so `options="read_only:true"` never had any effect on locking — a second process attempting to load the same database for reading, concurrently with any other open, failed with `Cannot lock Bingo database folder. Seems like it's already in use.` regardless of the read-only intent.

## Fix

- Parse `options` (specifically `read_only`) before requesting the directory lock in `load()`, so the lock request can actually depend on it.
- `tryGetDirLock()` now takes a `read_only` flag: when true it requests a shared lock (`LOCK_SH`), compatible with any number of concurrent shared-lock holders; when false (writers — `create()`, or a future non-read-only `load()`) it keeps the previous exclusive (`LOCK_EX`) behavior, so writers still correctly exclude concurrent readers and other writers.
- Stopped unlinking the lock file on release. `flock()` state lives on the open file descriptor/inode, not the directory entry, so removing the file was never required for correct unlocking — and it becomes actively unsafe once multiple readers can hold the lock concurrently: one reader's `close()` could unlink the file while a sibling reader still has it open, and a new arrival's `open(..., O_CREAT)` would then get a *different* inode with no contention against anyone, including a writer that should have been excluded.

## Scope

Single file, `api/c/bingo-nosql/src/bingo_base_index.cpp`. Both existing call sites (`create()`, `load()`) updated to pass an explicit `read_only` argument; no other callers of either function exist in the repo.

## Testing

Reviewed carefully by hand; I don't have a configured local build environment for this repo's full CMake/third_party toolchain, so I'm relying on CI here rather than claiming a local build+test pass. Happy to address review feedback or add a targeted test if there's a suitable existing harness for this file I should be using — pointers welcome.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dffe6bb47227`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
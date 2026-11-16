# Issue

**Title:** Fix: Passing wrong Zarr store that caused metadata consolidation error in upload_dataset()

## Description

## Changelogs

When consolidating the metadata locally, we were passing different stores which was throwing the error `memoryview: a bytes-like object is required, not 'dict'`. The fix was to append another `.store` when consolidating the metadata.

E.g., `dataset.zarr_root.store`  =>  <zarr.storage.ConsolidatedMetadataStore object at 0x13ddfaba0>
`dataset.zarr_root.store.store`  => <zarr.storage.DirectoryStore object at 0x13d900980>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6bc49ba47ea2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
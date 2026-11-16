# Issue

**Title:** #12704 – ketcher-standalone: Indigo worker never frees its embind objects (MapStringString / VectorInt), leaking WASM memory on every message

## Description

## Summary

Release the Indigo worker’s `MapStringString` options map and Calculate/Clean `VectorInt` objects in `finally` blocks, preventing WASM memory leaks on both successful and failed operations. Add cleanup regression tests and configure standalone Jest transforms for JavaScript and TypeScript.

## Evidence

The actual `indigoWorker.ts` message handler was exercised with real Indigo **1.49.0-rc.1** in separate fresh Node processes. Each run completed **200 successful Convert messages**, forwarding a monomer library option with approximately 1 MB of padding.

- **Before:** WASM memory grew from **32 MiB to 238.5 MiB**.
- **After:** WASM memory remained at **32 MiB**.

These measurements reflect WASM memory buffer capacity, not live allocation size.

All **10 regression tests pass** and fail when production cleanup is removed. Coverage includes successful operations, handler errors, and options/vector population failures. Standalone `npm test` passed formatting, lint, types, and tests; `git diff --check` passed.

Verified in the app: n/a — no visible editor change. Memory validation used the actual worker handler in Node; browser Worker transport and real VectorInt memory growth were not measured.

## Merge Danger

**Door:** two-way

The cleanup and test configuration changes can be reverted without data migration or public API changes.

**Blast Radius:** standalone

The shared options cleanup affects standalone worker commands used by both molecule and macromolecule modes. Calculate and Clean also release their selected-atom vectors. Premature cleanup could affect command execution, but objects are released only after the synchronous Indigo call returns or throws.

Monomer library forwarding, file format handling, and public APIs are unchanged. Remote mode does not use this worker. Browser editor flows and file format round trips were not separately tested.

---

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ccd85510302`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
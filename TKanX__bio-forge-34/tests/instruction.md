# Issue

**Title:** fix(web): Ensure Bond Connectivity is Exported in Web Application

## Description

### Summary:

Fixed a critical issue in the web application where exported PDB/mmCIF files lacked bond connectivity information (`CONECT` / `_struct_conn`), even when a topology had been successfully built. This was due to the exporter defaulting to structure-only serialization and the pipeline failing to persist the generated topology object. The fix ensures that the `Topology` object is correctly stored in the file state and utilized during export when available.

### Changes:

- **Enhanced File State Management (`file-store.ts`):**
  - Updated `FileEntry` type to include an optional `topology: WasmTopology` field.
  - Implemented `updateFileResult` action to store the generated topology alongside structure info after processing.
  - Added `clearFileTopology` to invalidate stale bond data when structure-modifying operations (e.g., cleaning, moving atoms) are performed.
  - Improved resource cleanup (`freeFileResources`) to ensure both structure and topology WASM objects are freed when files are removed, preventing memory leaks.

- **Updated Pipeline Execution (`executor.ts` & `use-processor.ts`):**
  - The `executePipeline` function now returns the generated `topology` object instead of just the bond count.
  - `useProcessor` now calls `clearFileTopology` before starting a run and uses `updateFileResult` to persist the new topology upon completion.

- **Corrected Export Logic (`exporter.ts`):**
  - Refactored `exportFileEntry` and `exportFilesAsZip` to use a helper `serializeFile` function.
  - `serializeFile` checks if a valid topology exists for the file entry. If so, it calls `topology.toPdbBytes()` / `topology.toMmcifBytes()` (which includes bonds) instead of the structure-only methods.

- **UI Updates (`file-card.tsx`):**
  - Updated the 3D viewer data source to use topology bytes when available, ensuring the visualizer also renders the correct bond graph.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79bb1d8923d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
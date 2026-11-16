# Issue

**Title:** fix(wasm): Prevent Template Ownership Transfer in Topology Builder

## Description

### Summary:

Fixed a critical issue in the WASM binding for `Topology::from_structure` where passing a vector of `Template` objects caused Rust to take ownership of the underlying data, preventing JavaScript from reusing or freeing those templates later. The fix involves cloning the internal template data for use by the `TopologyBuilder` and ensuring the vector's length is manually reset to zero to prevent the `wasm-bindgen` generated code from attempting to drop the now-moved elements, which would lead to a double-free or use-after-free scenario in the JS runtime.

### Changes:

- **Modified `Topology::from_structure` in `crates/bio-forge-wasm/src/lib.rs`:**
  - Changed the iteration over `templates` to clone `t.inner` instead of moving it. This ensures the original `Template` objects owned by the JavaScript side remain valid.
  - Added an `unsafe { tpls.set_len(0); }` block. This prevents the `Vec<Template>` destructor from dropping the individual `Template` instances (which are managed by JS) while still cleaning up the vector's own allocation. This is a necessary workaround for how `wasm-bindgen` handles vectors of complex objects passed from JS to Rust.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79bb1d8923d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
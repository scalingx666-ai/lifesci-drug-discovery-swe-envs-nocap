# Issue

**Title:** fix(vscode): select scalar ferrox WASM

## Description

## What changed

- Inspect every bundled `ferrox_bg-*.wasm` candidate and select the scalar build deterministically.
- Reject threaded artifacts by checking for a WebAssembly memory import before injecting the binary into the webview.
- Add regression coverage for threaded-first directory order and invalid artifacts.

## Root cause

CatGo v1.4.6 ships both threaded and scalar ferrox WASM artifacts. The VS Code extension used `ferrox_files[0]`, and the packaged directory order placed the threaded build first. Passing that binary to the scalar wasm-bindgen glue fails with:

```text
LinkError: WebAssembly.instantiate(): Import #0 "./ferrox_bg.js" "memory": memory import must be a WebAssembly.Memory object
```

The webview then fell back to fetching the bundled URL, producing the user-visible `HTTP status code is not ok` slab-generation error.

## Impact

VS Code slab generation now initializes the bundled scalar ferrox WASM regardless of filesystem enumeration order.

## Validation

- Targeted Vitest: `src/__tests__/ferrox-assets.test.ts` — 2 tests passed.
- Fresh Marketplace v1.4.6 package reproduced the old threaded-selection failure.
- Patched selector chose `ferrox_bg-Dcn6B0VW.wasm`; base64 transport preserved SHA256 `050ccb3bc1050366e8dd76a5f45ba3a327183bc1d57cacab57221c310f0519b3`.
- FCC Cu(001): 4 bulk atoms → 3 slab atoms, `pbc=[true,true,false]`.
- FCC Cu(111) p(3×3)×5: 45 atoms, 9 atoms per layer, surface-normal c vector.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e47256ac9501`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
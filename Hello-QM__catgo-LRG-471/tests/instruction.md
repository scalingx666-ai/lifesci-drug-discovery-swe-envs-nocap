# Issue

**Title:** fix(bonds): worker request deadline + solid_angle large-system downgrade

## Description

## Symptom

The 11k-atom kerogen `.data` file renders atoms but **never gets bonds** — in the Tauri window and in the web build alike, with any strategy selected. Small structures bond fine.

## Root causes

1. **`worker_request` has no deadline.** Structures >1000 atoms take the async worker path; a worker grinding `solid_angle` on 11k atoms (minutes on WebKitGTK, whose WASM tier is much slower than Chrome's) leaves the promise pending **forever** — the fallback chain (main-thread WASM → JS) never runs. Chrome escaped by accident: its worker failed to *init*, so it fell straight to main-thread WASM (12,668 bonds in 300 ms with atom_radii). A live-but-slow worker was worse than a dead one.
2. **`solid_angle` is inherently too slow at this size** on every engine, so even with a timeout the fallback would grind again on the main thread (and block the UI).

## Fix

- Size-scaled request deadline (`max(20s, 4ms/atom)`); on timeout the worker is **terminated** (state reset so it re-initializes on the next request — one huge request must not permanently disable the worker), the caller falls back, and the reason is logged.
- Above 8,000 atoms `solid_angle` is downgraded to `atom_radii` (one-time console note). On force-field-scale systems they agree closely — kerogen: atom_radii 12,668 bonds vs 12,648 in the file's own topology. Mirrors the VS Code extension's trajectory downgrade.

## Verification

Full suite: 4,414 pass. Kerogen browser check after merge: bonds in seconds regardless of the saved strategy.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55a8e6f43015`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
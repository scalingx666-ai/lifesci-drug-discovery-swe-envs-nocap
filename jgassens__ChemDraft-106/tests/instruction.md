# Issue

**Title:** Export loads images only from embedded data

## Description

SVG raster export now resolves image references only from embedded `data:` URLs. File URLs, absolute paths, relative paths, and other non-data references are refused by the usvg image resolver.

Adds a Rust regression test using a real local image fixture. Each path is XML-escaped and checked with both `href` and `xlink:href`; the parsed tree contains no image and the raster remains empty. Embedded data images remain supported.

The diff against upstream main contains only `apps/desktop/src-tauri/src/export.rs` and the build stamp in `apps/desktop/src/MainWindow.tsx` (`10.11.12.14-codex`).

Validation on Windows:
- `pnpm lint` — passed
- `pnpm vitest run packages/export-engine apps/desktop/src/coreCapabilityGrants.test.ts` — 54 passed
- `cargo fmt --manifest-path apps/desktop/src-tauri/Cargo.toml --check` — passed
- `cargo clippy --all-targets --manifest-path apps/desktop/src-tauri/Cargo.toml -- -D warnings` — passed
- `cargo test --manifest-path apps/desktop/src-tauri/Cargo.toml export` — 9 passed

macOS native checks and interactive export verification remain unverified.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf89f5f973b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
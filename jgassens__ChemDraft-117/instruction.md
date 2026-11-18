# Issue

**Title:** Raster export runs off the main thread and refuses oversized drawings

## Description

## Summary

PNG, JPEG, BMP, GIF and TIFF export (`rasterize_svg`) ran as a synchronous Tauri command, so it rendered on the main thread: a large drawing froze menus and palettes until it finished. The SVG also had no size limit before usvg parsed it (usvg limits tree depth and node count, not input bytes).

- Rendering now runs in `spawn_blocking`, like `list_system_fonts` already does.
- An SVG over **128 MiB** is refused before parsing with a specific message, e.g. "Could not export PNG: the drawing is too large to render (130.0 MiB of SVG; the limit is 128 MiB)." The limit fits two maximum-size embedded images (25 MiB each, about 33 MiB base64) plus 500 molecules at the largest fixture's size.
- Output for valid drawings is unchanged; the pixel-dimension cap is kept.

## Files changed

- `apps/desktop/src-tauri/src/export.rs`: async command, input size guard, tests.

## Tests run

- `cargo fmt --check`, `cargo clippy --all-targets -- -D warnings`, `cargo test` (242 passed) on macOS
- `pnpm lint`, `pnpm vitest run` (306 files, 6114 tests): pass

## Platforms

- macOS: packaged-build check to follow (export a large drawing as PNG; the app stays responsive)
- Windows: CI runs fmt, clippy and tests; real-input run to follow

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea3612c26f1f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
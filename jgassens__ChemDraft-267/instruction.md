# Issue

**Title:** Draw PNG pictures in image exports

## Description

## Summary

Image exports (PNG, JPEG, BMP, GIF, TIFF), Copy as PNG and plugin renders now draw pasted PNG pictures. Until now they were left out with a warning. Each picture lands at the same place, size, rotation and stacking order as in SVG and PDF export.

How it works:
- **Webview:** reads each PNG picture's header and enforces three limits per export: 16384 px a side, 256 MiB of decoded pixels, and 1024 pictures. It decodes pictures one at a time with `createImageBitmap` and sends straight RGBA to Rust as base64. Each picture in the SVG is replaced by a small stand-in.
- **Rust (`export.rs`, `export/pictures.rs`):** checks ids, sizes, the budget, the count and encoded lengths before unpacking anything. It then renders node by node: everything else through `resvg::render_node`, and pictures from the supplied pixels with `tiny_skia`, so clip paths and group opacity apply.
- **No native image decoder:** resvg stays without `raster-images`, and no image crates are added. Pages without PNG pictures take the unchanged `resvg::render` path.
- **Warnings:** the "pictures not included" warning now appears only for pictures that were not drawn, and names the reason: over 16384 px, over the 256 MiB budget, more than 1024 pictures, could not be decoded, or inside a mask, filter, blend mode or pattern. Copies of a picture made by reference are counted per copy.

## Known limitations

- An export near the 256 MiB decoded budget (for example one 8192 × 8192 picture) briefly uses about 0.6–1 GB of memory, because the pixels cross the IPC boundary as base64 inside JSON.
- Pictures inside a mask, filter, non-normal blend mode, pattern or marker are not drawn in image exports; they get a warning. SVG and PDF export include them.
- Checked by hand on Windows (WebView2); the macOS (WKWebView) hands-on run is pending.

## Tests

- New `apps/desktop/src/rasterPictureDecode.test.ts`; extended `rasterPictureExport.test.ts`.
- New Rust tests in `export.rs` / `export/pictures.rs`:
  - placement at scales 1 and 3 and at 90° rotation;
  - stacking order against plain resvg output;
  - group opacity and slice clipping, and gradient-stroked bare lines;
  - validation before unpacking;
  - per-reason and per-copy warnings, and forged stand-ins giving no warning;
  - shared filters read once, and a 500-deep mask chain on a small stack.
- Gauntlet on macOS at 471873f9 (after a second catch-up with main, at d3a65276, where only the build stamp conflicted; reviewed by Claude Opus 5.5 run-20261101-181117-680bd5 with no findings): all green, including `cargo test` and `pnpm build`. `pnpm vitest run`: 13445 passed. 2 tests timed out under machine load (`image.test.ts`, `workerChunks.test.ts`) and passed 36/36 when rerun on their own.
- Gauntlet on macOS at 39f5a243 (after the catch-up with main): all green. `cargo fmt --check`, `cargo clippy --all-targets -D warnings`, `cargo test` (672 passed), `pnpm lint`, `pnpm vitest run` (13331 passed, 0 failed), `pnpm build`, `git diff --check`.
- Earlier gauntlet on macOS at 540b7c50:
  - Rust: `cargo fmt --check`, `cargo clippy --all-targets -D warnings`, and `cargo test` (665 passed).
  - TypeScript: `pnpm lint` and `pnpm build`.
  - `pnpm vitest run`: 13329 passed. 2 failures are in `tools/agent-skill/stress/runner/runner.test.ts`, which this branch does not touch; they fail only under full-suite load and the file passes 57/57 on its own.

## Platforms

- Windows: hands-on PASS at 540b7c50.
  - PNG, JPEG, BMP, GIF and TIFF exports place the pasted picture in exactly the same box as the SVG export.
  - Copy as PNG is correct at 4×. The clipboard data was checked; pasting into Paint itself was not.
  - Pictures over 16384 px are refused at paste with a clear message. The largest accepted picture (16384 × 512) exports correctly, cropped to the page as on the canvas.
- macOS: tests and gauntlet pass; hands-on is pending.
- The Windows run found that TIFF exports declared "1 dpi". That came from main's TIFF writer, not this PR. It is fixed on main by #268, which this branch now includes.

## Reviews

- Kimi K3.1 Pro run-20261101-120516-7196cf: 7 findings, all fixed.
- Kimi re-review run-20261101-131115-7600ec: 2 findings, fixed.
- GPT-6 Astra run-20261101-143654-abba6d: 2 findings, fixed.
- GPT-6 Astra run-20261101-150650-dc0784: no actionable findings on the fixes or on the catch-up merge with main.
- Catch-up merge with main after #268 (39f5a243, written by Claude Sonnet 5.5, run-20261101-163028-335f84): only the build stamp conflicted. The TIFF resolution change from #268 and this PR's picture drawing combine cleanly: pictures are drawn into the image before every format is encoded, and TIFF and PNG declare the same density. Reviewed by Claude Opus 5.5 run-20261101-163113-69e73b: no defects.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b118011a828`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
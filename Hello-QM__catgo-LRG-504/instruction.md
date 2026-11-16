# Issue

**Title:** fix(export): cap image export to the real WebGL drawing buffer (fixes black-margin/cropped high-DPI exports)

## Description

High-DPI figure exports (PNG/PDF/etc.) came out with **black margins and a shifted, cropped structure** — the exported image was incomplete.

## Root cause

Browsers — especially WebKitGTK/Tauri — clamp the WebGL **drawing buffer** below the requested canvas size at a max-viewport/area limit that is *separate from, and far smaller than,* `MAX_RENDERBUFFER_SIZE`. On the repro machine the buffer hard-caps at **7838×4232** while `MAX_RENDERBUFFER_SIZE` reports 32768.

The exporter set `canvas.width` to the requested (high-DPI) size, but three then rendered into an oversized viewport while `gl.readPixels` read past the real buffer — so everything beyond the clamp came back black and the content was mis-framed.

## Fix

After `setSize`, detect when `gl.drawingBufferWidth/Height` fell short of the requested render size and scale the whole render plan (render dims, camera aspect, crop view-offset) down to the **actual** buffer, re-syncing `setSize`. Aspect is preserved, so a too-high DPI now caps at the largest correct image the GPU/browser can produce instead of corrupting it. Extracted `fit_plan_to_drawing_buffer` as a pure, unit-tested helper.

## Verification

- **Live (CDP):** a 12000px-wide export request produced **751,681 black pixels before** the fix and **0 after** (rendered at the real 7664×4328 buffer, content correctly framed).
- **Unit tests:** 4 new tests for `fit_plan_to_drawing_buffer` (fits-unchanged, scale-down-preserving-aspect, crop-offset scaling, no zero dims).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de6275dceaf8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
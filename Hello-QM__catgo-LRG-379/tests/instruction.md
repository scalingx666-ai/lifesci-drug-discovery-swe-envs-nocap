# Issue

**Title:** feat(voice): native backend STT — fix WebKit/Tauri OOM

## Description

## Problem

Terminal voice dictation ran Whisper **in the webview** via onnxruntime-web WASM. It works in Chromium but **freezes then white-screens the Tauri app** ("works at first, then blank", needs restart).

Root cause (measured, not guessed — via Playwright `webkit` = same engine as WebKitGTK/WKWebView):

| Engine | 6 sequential inferences |
|---|---|
| **Chromium** | flat **~644 MB** (reuses the WASM heap) |
| **WebKit/JSC** | **1 GB → 6 GB monotonic** (~0.8 GB/inference, never freed) |

WebKit/JSC never reclaims WASM linear memory between inferences; under cross-origin isolation (multithread → SharedArrayBuffer eager-commit) it ballooned to **9.7 GB → WebContent OOM-killed → blank window**. Single-thread does not fix it (still grows ~0.8 GB/inference). This is a WebKit-engine issue: **Linux WebKitGTK + macOS/iOS WKWebView affected; Windows WebView2 (Chromium) and the browser are fine.**

## Fix

Route dictation to a **native faster-whisper (CTranslate2) backend**, bypassing the webview entirely.

- **`server/catgo/routers/stt.py`** — `POST /api/stt/transcribe` (raw `<f4` 16 kHz PCM) + `GET /api/stt/health`. Auto device (CUDA float16 / CPU int8), `cpu_threads` up to 8, `hf-mirror.com` download fallback (for blocked HuggingFace). Registered as deferred `stt_router`. Dep `faster-whisper` added to pyproject + requirements.
- **`src/lib/gesture/backend-whisper.ts`** — `BackendWhisperEngine` keeps the tiny Silero VAD in-browser, POSTs each finished segment; `backend_stt_available()` probes health.
- **`terminal-voice`** picks the backend when reachable, else falls back to the WASM `LocalWhisperEngine`. Live model switch; the model menu hides the webview-only **Acceleration** control under the native backend.

### Also fixed alongside
- **Double input**: two panes both enabling voice spun up two MicVADs that both transcribed → duplicate keystrokes. Now a single global voice (starting one stops the other) + `start_vad` tears down its previous instance.
- WASM fallback forces single-thread on WebKit engines.

## Results (verified)
- Real speech round-trip (espeak → 16 kHz → backend): `"Hello world. This is a speech recognition test for Cat Go."` ✅
- Latency: **sub-second on CPU** for a 4.6 s clip (faster than real-time).
- User-confirmed in Tauri: **no more white-screen/OOM.**
- Native also unlocks small/medium models + GPU.

## Tests
- New `backend-whisper.test.ts` (7) + single-global-voice regression in `terminal-voice.test.ts`. Full vitest suite green (one unrelated `RdfPlot` timeout was machine-load flakiness; passes in isolation).

## Follow-ups (not in this PR)
- AMD/Intel iGPU acceleration via whisper.cpp Vulkan (this dev box = AMD Radeon Vega; faster-whisper GPU is CUDA-only).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a697fe29c84c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** feat(voice): local voice dictation in the terminal

## Description

## What

Adds **voice dictation** to the desktop terminal. A mic button + model/language/acceleration picker in the `TerminalWindow` toolbar lets you speak; speech is transcribed locally (in-browser, Transformers.js Whisper + Silero VAD) and the final transcript is typed into the active terminal's PTY at the cursor — **no Enter sent**. Inspired by [voxpilot](https://github.com/natearcher-ai/voxpilot), but built on CatGo's existing in-browser STT pipeline rather than its Node engine. Desktop only; mobile untouched.

## Highlights

- **Pure-data Whisper model registry** (`whisper-models.ts`): tiny/base/small (en+multilingual) + large-turbo, on-demand download, IndexedDB/Cache-Storage cached (no re-download next launch).
- **Generalized `local-whisper.ts`** to load any registry model id; existing gesture/chat callers unaffected.
- **`TerminalVoice` controller** (`terminal-voice.svelte.ts`): forwards only final transcripts, drops empties, trailing-space; engine injected for unit tests.
- **UI** in `TerminalWindow` (the real terminal toolbar — `TerminalPanel` is always embedded headerless): mic toggle + dropdown for model / spoken language / acceleration. Routes via `get_active_terminal().send_keys` (same path CatBot uses).
- **Chinese**: force language `zh` (auto-detect mis-transcribed Mandarin as English) + Traditional→Simplified via lazy `opencc-js`.
- **Engine robustness**: load onnxruntime-web wasm + Silero assets from a version-pinned CDN (Vite doesn't emit them → WebGPU-less machines 404'd); `device:'wasm'`+q8 by default because **q8-on-WebGPU hallucinates**; optional GPU path uses **fp16** WebGPU; anti-repeat generation params.
- **Speed**: cross-origin isolation (COOP=same-origin, COEP=credentialless — keeps CDN/HF fetches working) enables multi-threaded wasm, adaptive `min(8, cores-2)` threads.

## Tests

11/11 new unit tests pass (model registry, model-id threading, controller behavior). Type-check: no new errors.

## Reviewer notes / risk

- **COI headers are shared infra** (`vite.desktop.config.ts`, dev+preview, also affects mobile dev). COOP/COEP can affect cross-origin popups (OAuth) / embeds elsewhere — verified voice + model download work, but a broader app smoke is advisable.
- COI/multi-thread applies to vite-served contexts (dev/preview/`tauri dev`); the **production Tauri bundle** would need the headers on its own protocol for COI in the shipped app.
- Integrated-GPU WebGPU was unreliable for Whisper even at fp16 on the test machine → GPU path is opt-in, defaults to CPU.
- Spec + plan: `docs/superpowers/specs/2026-06-18-terminal-voice-input-design.md`, `docs/superpowers/plans/2026-06-18-terminal-voice-input.md`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b4598c71237`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** fix(voice): cancel in-flight VAD start so the mic can't get stuck on

## Description

## Bug
Terminal (and chat/gesture) voice could not be turned off — toggling the mic to "off" left it still capturing and dictating ("变灰了还在输入 / 关不掉"). Confirmed on the Linux desktop (WebKitGTK).

## Root cause
`start_vad()` does `vad_instance = await MicVAD.new(...)`, which loads a worklet + the Silero ONNX model from a CDN (slow). `stop_vad()` only tore down a non-null `vad_instance`, so a stop that landed **while `MicVAD.new()` was awaiting** was a no-op — then `new()` resolved and called `.start()`, spinning the mic up **after** stop, with the toggle visibly off and no live instance left to stop it. Same failure class the file's hot-reload guard already handled for reloads.

## Fix
`vad.ts`: a generation counter bumped by every `start_vad`/`stop_vad`. A start captures its generation and, if superseded (a stop or a newer start) by the time `MicVAD.new()` resolves, destroys the fresh instance instead of starting it. Fixes all three engines that share this VAD singleton (terminal, chat-gesture, local/backend whisper). Gesture tests pass (23).

Verified on-device: rebuilt Linux desktop, terminal mic now stops cleanly on toggle-off.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a7c4015661d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
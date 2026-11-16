# Issue

**Title:** fix(mobile): Android insets + CJK terminal input + voice transcript edits

## Description

Fixes a batch of mobile input bugs reported on-device (RMX2111, Android), several cross-platform. Verified on-device where marked ✅.

## Bugs fixed

### Android window insets — `d36356e` ✅ device-verified
Every released APK (incl. 1.2.1) shipped a **stock** `MainActivity` because CI's `tauri android init` regenerates the gitignored `gen/android/` from stock templates and **never re-applied** the inset patch. Result: header drawn under the status bar (clock/battery overlap) and the soft keyboard covering the terminal keybar / AI-chat composer.
- `deploy/android/overrides/MainActivity.kt` (canonical, committed) + `deploy/android/apply-native-patches.sh` (idempotent) run by `android-build.yml` after init, before build.

### Terminal CJK input — last word dropped — `d4a7db3` ✅ device-verified
On-device trace showed each committed Chinese word arrives as a collapsed `insertText` with **no composition events**. The IME guard buffered every CJK `insertText` and flushed only on the *next* event, so the **last word was silently dropped** ("type 你好你好 → only one 你好"). A complete CJK ideograph delivered as collapsed `insertText` is final → write it on arrival; keep buffering only for Hangul (Korean jamo rebuild). Mobile + desktop, 3 regression tests.

### Terminal — Backspace swallowed by the CJK IME guard — `f850e50`
WebKit fires `compositionend` unreliably for CJK, so `std_composing` could stick and the guard ate every DEL — couldn't delete Chinese. Backspace now always passes through; dropped `\x7f` from `IME_CONFIRM_KEYS`. Mobile + desktop, regression test.

### Voice transcript clobbered edits — `293e5b6` (mobile) / `361e954` (desktop)
Speech `onresult`/`apply_transcript` rewrote the whole input each event, wiping a user edit/deletion. First real edit now freezes transcript application. Mobile composer also floats above the iOS keyboard via `visualViewport` (B1).

### whisper.cpp on mobile — dropped — `0bd75e2`
Built-in OS keyboard dictation is sufficient; design doc retained with the decision recorded. In-app iOS SFSpeech mic left as-is (multi-sentence overwrite = WONTFIX).

## Verification
- Unit tests green (terminal-ime: 14); type-check clean for changed files.
- On-device (RMX2111): status-bar overlap fixed, keybar floats above keyboard, full CJK phrase "你好 朋友 你好 朋友" renders.
- A-chat / B1 verified by code + shared mechanism (composer float uses the same native inset as the verified keybar); live chat needs an API key to view the composer.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8f5071361d3b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
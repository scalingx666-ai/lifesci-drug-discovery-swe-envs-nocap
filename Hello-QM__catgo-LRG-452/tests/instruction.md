# Issue

**Title:** fix(mobile): iOS terminal Chinese dictation duplicated the transcript

## Description

## Problem

On iOS, dictating **Chinese** into the mobile terminal produced garbage (the transcript re-appended on every recognizer refinement), while dictating **English** worked fine.

## Root cause

iOS dictation streams Chinese exactly like English — `insertText` `beforeinput` events that **replace** the previous partial transcript. But in `MobileTerminal`'s `beforeinput` handler the IME guard runs **first**, and `terminal-ime.ts` treats any CJK `insertText` as an Android-style final IME commit:

- it writes the **full partial** to the PTY on arrival → every refinement re-sends the whole transcript (`你` + `你好` + `你好世界`), and
- it `preventDefault()`s → the textarea never accumulates the running transcript, so the dictation-reconcile path (which makes English work) is starved of its diff base.

## Fix

- `terminal-ime.ts`: new `bypass_cjk_insert_text` option — flush any pending buffer, then return non-Hangul CJK `insertText` to the caller unconsumed. Hangul keeps buffering (typed jamo are rebuilt via `insertReplacementText`).
- `MobileTerminal.svelte`: pass the flag on iOS; the dictation-reconcile branch now also accepts CJK `insertText` with a **collapsed** caret (the first partial is a plain insert — reconcile degenerates to an append and the textarea keeps the transcript for the next diff).
- `transport/index.ts`: add `isIOS()` (handles iPadOS desktop-class UA).

Android write-on-arrival behavior and desktop terminal are unchanged.

## Tests

- Guard: bypass returns CJK `insertText` unconsumed, still buffers Hangul, flushes pending Hangul before handing over, leaves Pinyin composition + Latin untouched.
- `reconcileReplacement`: CJK first-partial append, refinement tail-send, mis-heard-character correction.
- `vitest run`: 2047 tests pass (file-level failures identical on main — sandbox network noise).

Needs on-device verification (TestFlight build) — Chinese + English dictation into an interactive shell prompt.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `481e4de8f947`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
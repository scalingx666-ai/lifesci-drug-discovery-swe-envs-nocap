# Issue

**Title:** Skip state updates when a plugin command settles after unmount

## Description

## Summary

A plugin command's promise can settle after the document window has unmounted: a real window can close while a command runs, and on Windows CI `canvasContextMenu.dom.test.tsx` ended with an unhandled rejection, `ReferenceError: window is not defined`, thrown from `MainWindow.tsx`'s `invokePluginCommand(...).catch(() => setStatus(...))` after the test environment was torn down. An unhandled rejection fails the whole Vitest run, so it was hitting unrelated PRs (seen on #238).

`MainWindow` now keeps one mounted ref. Every asynchronous completion of a plugin command that sets React state (the immediate path's error status; the queued path's result, error and pending-command bookkeeping) skips the state update once the window has unmounted. Refs are still cleaned up, so nothing leaks. While mounted, a failing command still shows `Command failed: …` exactly as before.

## Tests

- New `apps/desktop/src/pluginCommandUnmount.dom.test.tsx`: holds a command open, unmounts, settles it, and asserts no late state update and no unhandled rejection, for both the immediate and the queued path, plus the mounted error message. It fails on the code before this change.
- `pluginCommandUnmount`, `canvasContextMenu` and `MainWindow.plugins` DOM suites: 128/128 on macOS. CI's four checks run the full suite on Linux, macOS and Windows.

## Review

Opus at high effort (agentctl run-20261028-144418-43dabf): every plugin-command completion that sets state is covered; correct under React StrictMode double-mounting; the test is not timing-dependent and restores its listeners and globals. Approve.

Follow-up commit `8d278025`: the mounted ref starts `true` (the effect still restores it after a StrictMode remount and clears it on cleanup), removing a brief window before the first effect flush where it read false while mounted; same pattern as the file's `assistantHistoryMountedRef`. Opus low review (run-20261028-144811-a13590): approve.

## Follow-up (not in this PR)

- Plugin-runtime callbacks (patch and status callbacks around `MainWindow.tsx:10780`) can still update state after unmount; disposing the plugin runtime on unmount is a separate change.

## Platforms

Shared TypeScript in the desktop window; no native, menu, shortcut, clipboard or path code. Verified on macOS; Windows runs in CI (the failure this fixes was seen there).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d728d6e80a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
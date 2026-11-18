# Issue

**Title:** Tauri events: stopping a listener can no longer raise the crash dialog

## Description

## Summary

**"ChemDraft ran into an error (Cannot read properties of undefined (reading 'handlerId'))", on Windows, at launch.** The owner hit it twice today in branch builds, and it is on `main`.

### Cause

Tauri 2.11.2, which the app uses (`tauri` 2.11.2 and `@tauri-apps/api` 2.11.0):
- `listen()` resolves on the IPC reply. The page entry it later unlistens by, `__internal_unstable_listeners_object_id__[event][eventId]`, is created by a script that Rust evaluates separately, and that script can land after the reply.
- Unlisten reads `.handlerId` from that entry with no guard (`unlisten_js_script`; 2.12.0 adds the guard).
- So an unlisten made in that gap throws inside an async function. That is an unhandled rejection, which the crash reporter shows as the dialog, and the native listener is never removed.
- 2.11.2 never deletes an entry, so this is not a double unlisten. It is an unlisten that runs too early.

### Trigger

The `toolset-layout-edit` listener effect in `MainWindow` depended on `[commitToolbarLayout, setCustomizeMode]`. Both change once native-palette mode settles after startup, so every cold launch subscribed, unlistened right away and subscribed again. A production build of `main` registers that listener **3 times per launch**.

### Fix

- **`window-manager/tauriEvents.ts`:** `safeTauriListen`, `listenTauriEvent` and `listenCurrentWindowEvent`. The returned stop:
  - mutes the handler at once;
  - runs Tauri's unlisten exactly once, after `listen()` has resolved, and a stop made earlier is applied then;
  - retries an unlisten that throws or rejects up to 6 times (5 retries, 25/50/75/100/125 ms apart), then gives up with a console warning, never a rejection.

  `TODO(tauri-events)`: drop the retry once the tauri release we use includes the unlisten guard (upstream dev has it; not confirmed for 2.12.0). No Tauri upgrade here: the crate and the package would have to move in lockstep on both platforms, which is a decision of its own.
- **Every Tauri listener goes through it, 30 sites:**
  - `window-manager/index.ts` (25, including the quit-flush window listener);
  - `plugins/panelBridge.ts` (4);
  - `conformerDebug.ts` (1);
  - `MainWindow.tsx` (1).

  So palettes, popovers, the tooltip and plugin windows are covered too.
- **The trigger:** the `toolset-layout-edit` effect reads both callbacks through refs and subscribes once.

## Evidence (Windows)

- **Reproduced in the app.** I used a dev instance under its own identifier, so nothing touched the owner's apps, with WebView2 CDP and Tauri's `unregisterListener` wrapped from document creation (so it fails as 2.11.2 does), then reloaded the document window 40 times.
  - On `main`: 23 unlistens before the entry existed, and 23 unhandled rejections reading `'handlerId'`. The stacks point to `toolset-layout-edit`, plus StrictMode's double effects in dev.
  - With this PR: 29 such unlistens (the race itself is Tauri's) and **0 unhandled rejections**. Each retried unlisten succeeded once the entry landed.
- **Subscriptions per load:** after one load in dev, all 21 main-window events register exactly StrictMode's 2. `toolset-layout-edit` was 4–6 before this PR.
- **On a production build:**
  - Tonight's close-timing A/B, with release builds launched 64 times on a busy machine, raised the real crash dialog once from `main`'s build and never from this branch's build.
  - In the close-cycle harness, `main`'s release build registered `toolset-layout-edit:3` per launch in all 30 cycles.

## Tests

- **`window-manager/tauriEvents.test.ts`.** 9 tests against a faithful Tauri 2.11.2 fake: `listen()` resolves first, the page registers later, and unlisten reads the entry only once the event has a bucket of entries, then rejects if this entry is missing. That is the case after another listener of the event has registered; the very first listener of an event name does not throw. The tests:
  - reproduce the original crash;
  - stop called 3× removes the listener once;
  - a stop made before `listen()` resolves is applied when it does;
  - a stop in the registration gap rejects at Tauri, is retried, and removes the listener;
  - the first listener of an event name: in the gap Tauri reads nothing and does not throw, so stop removes it at once, with no retry or warning;
  - stop mutes the handler;
  - after 6 attempts it gives up with a console warning;
  - an attach failure rejects `attached`;
  - a synchronous throw is handled.

  An unhandled-rejection listener asserts that none escapes.
- **The same file has a source scan.** It fails on any `listen` or `once` from the event module (named import, dynamic import, `.then` destructure), any `.listen(` or `.once(` call (a window held in a variable, `getByLabel(...)`), or a Tauri window helper (`onFocusChanged`, `onCloseRequested`, …) outside `tauriEvents.ts`. A self-test checks that each direct form is caught and that the app's own helpers are not.
- **`docs/manual-stress-checklist.md`:** cold launch ten times on Windows, with no crash dialog.

## Platforms

- **Windows:**
  - `pnpm lint` ✅.
  - Full `pnpm vitest run` in the heavy slot ✅: 279 files, 5330 passed, 0 failed. That ran on `b3b44c6`, whose TypeScript is identical to this PR's (it differs only in `lib.rs` and the checklist, both of which belong to the close-hang branch).
  - Focused re-run on `1dadf75` ✅: 9 files, 67 passed; on `3e0e200`, `tauriEvents.test.ts` ✅ 12 passed and lint ✅.
  - `git diff --check` ✅.
  - No Rust changed; the Rust gates run in CI.
  - The in-app repro and A/B above.
- **macOS:** not verified. This is platform-neutral TypeScript, and the race is in Tauri's shared event script. Check for no crash dialog over cold launches and quits.

The close hang that sometimes followed this dialog (b) is a separate bug with its own cause, and is being fixed on its own branch.

## Gates

- [x] Stress test (repro, the 40-reload before/after, the gauntlet)
- [x] Review: claude-fable `fable-pr96-20261010`, high effort: APPROVE. It confirmed the root cause against the Tauri 2.11.2 source and the state machine at every edge. The follow-ups are in `3e0e200` (wider scan, first-listener case, TODO wording); re-review `fable-pr96-rr-20261010` APPROVE.
- [ ] macOS check
- [ ] Owner hands-on check

## Squash-merge message

```
Tauri events: stopping a listener can no longer raise the crash dialog

"ChemDraft ran into an error (Cannot read properties of undefined
(reading 'handlerId'))" came from Tauri 2.11's unlisten, which reads the
page's listener entry with no guard. listen() resolves on the IPC reply,
while the script that creates that entry is evaluated separately and can
land later, so an unlisten in that gap threw an unhandled rejection and
left the native listener in place. The toolset-layout-edit listener hit
that gap at every cold launch.

A shared helper (window-manager/tauriEvents.ts) now backs every Tauri
listener: stop mutes the handler, runs Tauri's unlisten once after
listen() resolves, and retries one that fails, never leaving a rejection
unhandled. The toolset-layout-edit listener subscribes once. A source
scan keeps direct listens out.

```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3edb981575ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
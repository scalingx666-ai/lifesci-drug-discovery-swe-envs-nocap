# Issue

**Title:** Windows: closing the document window quits within seconds of saving

## Description

## Summary

**On Windows, closing the document window sometimes saved the session at once but did not quit for 10 s to 2 min** (once force-killed). The next launch then handed itself to the dying process through the single-instance lock. AGENTS.md §1 requires that closing the document window quits after flushing.

### Cause

From a diagnostic build that logged, per process, the close, the flush, the quit and every window build:

- `request_quit` asks the document to flush. Its answer (`quit_after_flush`) or a 3 s grace calls `quit_now` → `app.exit(0)`, which only **asks** the event loop to stop. The event loop runs on the main thread.
- Every WebView2 is built on the main thread. Palettes, the tooltip and the two prewarmed color-picker popovers are built after launch, through async commands that Tauri marshals there.
- On a busy machine a single build took **12.1 s**. In one logged close:
  - the flush was confirmed 0.12 s after the close, so the session was saved;
  - `ExitRequested` arrived only 7.1 s later, when that build released the main thread;
  - a further build had been queued meanwhile.
- In another (main's build), a color-picker popover was built 3.8 s **after** the close, and teardown waited for a second build: 10.9 s in all.

### Fix (`lib.rs`, `ocsr_engine/mod.rs`)

1. **No new windows once a quit has begun.** `lock_window_creation()` returns `Result` and, after taking `WINDOW_CREATION`, refuses with "ChemDraft is quitting; no new windows" once `QUIT.requested` or `APP_QUITTING` is set. A request queued behind a build in progress is refused too. Its 7 callers use `?`:
   - `open_toolset_window`, `open_plugin_panel_window`, `open_toolset_popover`;
   - `prewarm_toolset_popover`, `prewarm_toolset_tooltip`;
   - `toggle_spin3d_debugger_window`, `toggle_preferences_window`.

   The JS callers already handle a refusal: the prewarm callers catch, the reconciler treats it as `open: false`, and the popover and panel opens catch. The diagnostic log shows builds refused during quits (1–2 per slow process). Each would otherwise have held the main thread for 0.5–12 s.
2. **An exit watchdog (Windows).** `quit_now` arms it once, and nothing else does. That is only when the quit is decided: the session flush has been confirmed, or its 3 s grace has run out. If the event loop has not ended the app 2 s later (`EXIT_WATCHDOG`), the watchdog thread:
   - writes one stderr line: `ChemDraft: forced exit <how the quit was decided>; event loop did not exit within 2 s`, where the middle names the path: `after the session flush was confirmed`, `after the flush grace expired (session flush not confirmed)`, or `with no document window to flush`;
   - kills the OCSR install's uv tree and sidecar at once (`OcsrEngineState::kill_for_forced_exit`, then the usual `shutdown`);
   - ends the process with `TerminateProcess` (see below).

   So once the app has seen the close, it exits within flush + 2 s, whatever holds the main thread.

   **TerminateProcess, not `std::process::exit`.** On Windows `process::exit` is `ExitProcess`, which runs every DLL's detach. WebView2's Chromium spent about 3 s tearing down there (`Failed to unregister class Chrome_WidgetWin_0` in stderr) and once raised a dialog. The session is already written, the OCSR children are killed and stderr is unbuffered, so nothing is left for a detach to do.
3. **`quit_after_flush` is `async`.** As a sync command it ran on the main thread, so while a window build held that thread, the document's answer waited too, and the quit and the watchdog only started when the 3 s grace ran out (flush + 5 s). On a worker, the answer decides the quit at once.

   **Thread safety.** Everything the decision touches works from any thread:
   - the flags are `AtomicBool` with `SeqCst`;
   - the watchdog is a `thread::spawn` of a `QuitHost: Clone + Send + 'static` host;
   - `AppHandle::exit` posts the exit request to the event loop and returns (`AppHandle` is `Send + Sync` and documented as usable from any thread);
   - `OcsrEngineState` is managed state, so `Send + Sync`, and its kill paths use atomics and mutexes;
   - `TerminateProcess` is safe from any thread.

   A test checks `QuitFlow`, `AppHandle<Wry>` and `OcsrEngineState` are `Send + Sync` at compile time.
4. **A second launch while quitting is ignored.** The single-instance callback (Windows) first asks `second_launch_action(quit_in_progress(), setup_completed)`. Once a quit has begun it opens no document and shows or rebuilds no window, since either would be lost with the process and would hold the main thread the quit waits on. It logs `ChemDraft: a second launch arrived while quitting; ignored (this process is exiting)`. A launch after the exit starts a fresh process.
5. **A testable quit flow.** The state and timings live in `QuitFlow` (the app's is `QUIT`), and the app's actions are behind a `QuitHost` trait. Tests drive the real flow with a fake host and their own flags.

**No quit is ever cancelled.** `requested` and `quitting` are never cleared: the app never prompts to save, a relaunch is a new process, and the Windows updater's `install()` ends the process itself.

### Exit-time audit: what a forced exit skips

On Windows, Tauri's normal exit ends the process with `std::process::exit` too (tao `event_loop.rs:230`), after `RunEvent::Exit` and `cleanup_before_exit`. So Drop of managed state isn't guaranteed even today.

| Exit-time action | Handling |
|---|---|
| **Updates** | Windows (tauri-plugin-updater): installs only when the user accepts (`appUpdates.ts` saves the session, then calls `install()`, and the plugin itself `exit(0)`s), so there's no install-on-quit and nothing is staged. macOS (Sparkle): `SUAutomaticallyUpdate` is false and nothing installs at termination; the watchdog doesn't run there anyway. |
| **Window and palette frames** | Written on every move and resize (`persist_main_window_geometry`, palette positions). The open-palette set is saved by the frontend as it changes. Nothing is written at exit, and `APP_QUITTING` (set first) suppresses teardown events. |
| **Plugin storage** | Written to `plugins/<id>/storage.json` as it changes, with a 250 ms frontend batch. A change in the last 250 ms is lost on any quit, normal or forced; that's an existing gap, not new. |
| **Logs** | No log crate, file logger or buffered writer; `eprintln!` is unbuffered. |
| **Drop impls** | `OcsrEngineState` → `shutdown` **must run**. Its sidecar runs in its own process group with no job object, and uv is killed by tree. The watchdog therefore kills both directly before exiting: `shutdown` runs once, and if the main thread is already in it, the sidecar has been sent Shutdown and loses its stdin with the process. `CaptureTempFile` / `TempImage` may leave a temp folder or file, as a crash would. `PartialGuard`'s unfinished install folder is removed at the next launch. `OpenedClipboard` is released by Windows. |
| **Interactive 3D sidecars** | No exit handler at all: they're stopped only by the stop command or a new session, and otherwise end on stdin EOF. Same under either exit. |
| **WebView2 storage** | localStorage holds keybinding, spin3d, disabled-plugin, arrow-style and last-update-check values, written only when the user changes a setting, never at quit. WebView2 commits it in its own browser process (`msedgewebview2.exe`), which ending ChemDraft's process does not end. **Measured** ("Review round" below): a value written 150 ms or 1.5 s before the close was there on an immediate relaunch 10/10 on the forced path and 40/40 on the normal path. |
| **Plugins and Tauri** | single-instance's mutex and message window, and `cleanup_before_exit`, are released by Windows with the process. tauri-plugin-http saves its catalog-fetch cookie jar at Exit; skipping that is safe. No tray, no global shortcuts. |

### Platforms

The main-thread WebView2 build is a Windows problem, and **macOS never reaches `quit_now`**: closing the document window hides it, and Quit is the application menu's, through NSApplication termination, which Sparkle relies on.
- `QuitHost::force_exit` is `#[cfg(windows)]`.
- Its `#[cfg(not(windows))]` side only logs and leaves the exit to the event loop.
- `kill_for_forced_exit` is allowed dead on non-Windows.
- `request_quit_with`, `ask_document_to_flush` and `flush_grace` carry the same `cfg_attr(target_os = "macos", allow(dead_code))` that `request_quit` and `QUIT_FLUSH_GRACE` already had.

### Not fixed: closes before the document webview exists

A close made in the first seconds after launch on a busy machine, while setup is still building the document window's webview, never reaches the app's close handler. That process exits once setup finishes (8–25 s under load in the log). There's nothing to save at that point. It's documented here, not changed.

## Tests

`lib.rs` tests, with a fake host whose event loop never ends the app:
- a requested quit only asks for the flush; no exit and no watchdog until it's confirmed;
- a confirmed flush → `exit` → the watchdog's forced exit;
- an unanswered flush quits after its grace (400 ms, so preemption cannot let it run out before the first check), then the forced exit;
- with no document window to ask, the quit is decided at once;
- repeated closes and confirmations ask once and arm one watchdog, and the flow is never cleared;
- the watchdog is armed before the exit request, so a busy main thread cannot stop it: the fake host's `exit` needs the "main thread", which the test holds busy, and the forced exit must still come while the worker is stuck in `exit` (requesting the exit before arming fails this test: `["exit"]` instead of `["exit", "force exit"]`, checked by mutation);
- the forced-exit line names each path, and each path (confirmed flush, grace expired, no document) hands its reason to the watchdog;
- `quit_after_flush` stays an `async` command (Tauri runs those off the main thread);
- a second launch while quitting opens and shows nothing (all four quitting × setup cases);
- everything the decision touches is `Send + Sync`;
- window creation is refused once a quit is requested.

`docs/manual-stress-checklist.md`: a quit and close timing entry for both platforms.

## Stress (Windows)

### Deterministic: the B condition reproduced on demand

This used a proof-only build (never pushed). It is this PR plus two env switches: `CHEMDRAFT_QUIT_STALL_MS` posts a 10 s sleep to the main thread when the document confirms its flush, exactly what an in-flight WebView2 build does, and `CHEMDRAFT_QUIT_NO_WATCHDOG` runs without the watchdog, as before this PR.

Each cycle: launch, WM_CLOSE to the document window 8 s later, then time the session write and the process exit. 3 s after the close, launch again, to see whether that launch gets a fresh process or is handed to the dying one. Any `#32770` dialog of the process is recorded with its title and text.

| 10 cycles each | flush → exit | relaunch 3 s after close | warning line | dialogs after the close |
|---|---|---|---|---|
| watchdog off (before) | 10.01–10.08 s, median 10.03 | handed to the dying process 10/10 | 0 | 0 |
| **watchdog on (this PR)** | **2.06–2.17 s, median 2.08** | **fresh process 10/10** | **10/10** | **0** |

The stderr line, every time (then worded): `ChemDraft: the app had not exited 2.0 s after quitting (the main thread was busy); ending the process`. It now names how the quit was decided (see the Fix section).

**How the proof got here:**
- **Run 1** used `std::process::exit` and a sync `quit_after_flush`: flush → exit 4.90–5.15 s, with 1 dialog after a close.
- **Run 2** used `TerminateProcess`: still 4.96–5.20 s, 0 dialogs. The extra 3 s was the grace, because the sync command waited for the busy main thread.
- **Run 3** is this PR.

Two dialogs appeared in run 3, one in each mode. Both were **already up at launch, before any close**: "Send a crash report?" (Email Report / Not Now), ChemDraft's own crash-reporter confirm for an uncaught error at cold launch. This branch does not include #96, so this is almost certainly the `handlerId` cold-launch crash that #96 fixes, and it is independent of the watchdog. The dialog's message is in a task-dialog control the capture could not read; only the title and buttons were recorded.

### Natural: fixed-delay closes under load

Release builds of `main` and of this branch (the build was of `f291a0b`, before `TerminateProcess` and the async command), alternating, closing 2–9 s after launch, 4 rounds, under a concurrent full vitest:

| 32 closes each | exit after close: within 2 s / median / p90 / max | closes the app saw (session written): flush → exit median / p90 / max | closes before the app could see them | dialogs |
|---|---|---|---|---|
| `main` | 26 / 0.19 / 2.43 / 9.29 s | n=25: 0.00 / 0.08 / 0.52 s | 7 | 0 |
| this branch | 20 / 0.27 / 4.18 / 10.07 s | n=25: 0.06 / 0.22 / 2.22 s | 7 | 0 |

**In this run the B hang did not occur on `main`:** every close `main` saw exited within 0.52 s of its flush. So this run can't show an improvement. Overall p90 and max on both sides come from closes made before the document webview existed (see "Not fixed" above), which neither build can change. The branch's single 2.22 s case is the watchdog's bound. Earlier runs on `main` did show B:
- in the diagnostic log, a 7.1 s close-to-exit after a confirmed flush, behind a 12.1 s build;
- in a first A/B, `main` exits of 11.8–13.6 s.

Earlier, a 15-cycle harness run on `main` (capture on all 6 pages, drawing, a label and an undo before each close) exited in 1.3–16.3 s, with only 3 of 15 within 2 s.

## Review round (`0b3cfc1`): storage, fire rate, second launch

These checks used proof-only builds (never pushed): this PR plus the two env switches described above, with their own identifier and a WebView2 debug port, so no other ChemDraft window was touched.
- The forced-path storage run and the first 20 normal trials used the earlier proof build (`32698f6`'s quit code; old log wording, no second-launch gate).
- The second 20 normal trials and the second-launch checks used a build of `0b3cfc1`. Each trial:
1. launch;
2. write a localStorage marker in the document page;
3. post WM_CLOSE to the document window 150 ms or 1.5 s later (alternating);
4. time the exit and count forced-exit lines on stderr;
5. relaunch at once, read the marker back, and close that instance too.

Exit times are measured from the start of the WM_CLOSE post, so they include 1–3 s of PowerShell startup.

**localStorage survives both exits.**

| Path | Trials | Marker on relaunch | Forced-exit line | Exit after WM_CLOSE |
|---|---|---|---|---|
| Forced (main thread stalled 10 s at the quit) | 10 | 10/10 | 10/10 | 3.36–4.47 s |
| Normal | 40 | 40/40 | 0/40 | 1.45–5.03 s |

WebView2 writes localStorage from its own browser process, which ending ChemDraft does not stop. So no flush before arming the watchdog is needed.

**Watchdog fire rate on natural closes: 0.** Load is taken from the shared heavy-job slot, which another session's release builds held during part of the runs.

| Condition | Closes (primary + relaunch) | Forced exits |
|---|---|---|
| Idle (slot free) | 12 (6 + 6) | 0 |
| Under a concurrent release build (slot held) | 68 (34 + 34) | 0 |
| **All** | **80** | **0** |

**Second launch while quitting, in the real app.**
- **Main thread free.** The document page's JavaScript was held busy for 2.5 s, so its flush answer waited. A second launch with a document path was made 300 ms after the close.
  - In 3 of 4 trials the dying process logged `a second launch arrived while quitting; ignored`. It made no attempt to open the document and showed no window, and the second process handed off and exited. The first then exited normally, without a forced exit, and a third launch started a fresh app.
  - In the 4th trial the second launch reached the lock after the first had released it, so it became the fresh app itself.
- **Known limit: main thread stalled** (the 10 s stall switch). The callback cannot run at all. tauri-plugin-single-instance hands off with a blocking `SendMessageW(WM_COPYDATA)` to a window on the first process's main thread. The second process therefore waits until the watchdog ends the first process, at most flush + 2 s, then exits, and that launch is lost without a log line (3/3 trials). A launch after that starts fresh. Fixing it would mean releasing the single-instance lock off the main thread while the old WebView2 browser process may still hold the user-data folder. That is not done here.

## Platforms

- **Windows:**
  - `cargo clippy --all-targets -D warnings` ✅;
  - `cargo test` ✅ 219 passed on `c0d741d`'s code, including the 10 quit, second-launch and window-creation tests;
  - `cargo fmt --check` ✅;
  - `pnpm lint` ✅;
  - `git diff --check` ✅;
  - the release builds ✅ and the stress runs above.
  - **Full `pnpm vitest run`** (on `f291a0b`, whose TypeScript is identical: this PR changes only the stamp there): 5318 passed and 2 failed, while the A/B was launching apps alongside. `toolsetBridge`'s stress route is load-sensitive (HEAVY-SLOT.md). `MainWindow.smilesPaste` lost its status line to the late "Native toolset windows unavailable" message, the race #95 fixes. Both files pass 33/33 twice on their own.
- **macOS:** not verified here. The master session runs a ⌘Q/osascript quit-timing check: launch, wait 2 s, quit, measure the exit, 10 cycles plus one with a palette open.

## Gates

- [ ] Stress test (above)
- [ ] Review (claude-fable, high effort)
- [ ] macOS quit timing
- [ ] Owner hands-on check

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c3899817b2a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
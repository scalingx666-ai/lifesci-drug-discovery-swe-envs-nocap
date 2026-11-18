# Issue

**Title:** Opening a document with ChemDraft closed no longer crashes on macOS

## Description

## Summary

On macOS, double-clicking any `.chemdraft` file while ChemDraft is not running crashed the app about half a second after launch (0.3.9 and `main`). macOS hands the app the document (`RunEvent::Opened`) before Tauri creates its config windows. `deliver_opened_document` then built the `main` window itself, Tauri's setup failed with `a webview with label 'main' already exists`, and the panic aborted inside an AppKit callback.

The fix records opened documents until setup has completed (an explicit flag, because macOS can close every window afterwards). Setup shows the config window, and its mount drains the pending document, which is the path that already existed. The Reopen handler and the single-instance callback also wait for setup, and the Windows/Linux launch-argument open runs at the end of setup.

## Files changed

- `apps/desktop/src-tauri/src/lib.rs`: setup-completion gate, `OpenDocumentDelivery` decision, three unit tests
- `docs/manual-stress-checklist.md`: cold-launch file-open check for Finder and Explorer
- `apps/desktop/src/MainWindow.tsx`: build stamp `10.10.8.29-codex`

## Tests run

- `cargo fmt --check`, `cargo clippy --all-targets -- -D warnings`, `cargo test` (macOS): pass, 226 tests
- Packaged branch build (`./run-app`, label `cold-open [fix/macos-cold-open-crash]`): quit the app, then `open -a` it with a `.chemdraft`. The app stays up, no crash report is written, and the saved document session holds the opened file byte for byte. On the released 0.3.9 the same step aborts every time, with two different files.

## Platforms

- **macOS:** verified as above.
- **Windows:** unverified. Needs: clippy and tests on Windows, then with ChemDraft quit, double-click a `.chemdraft` in Explorer (opens with that document); then, with it running, double-click another (single-instance handoff still opens it).

## Known limitations

A gap that predates this change, found in review: a document opened while the app is already running, in the moment between the window draining the pending slot and registering its listener, is emitted to no one and stays unopened until a remount. This change does not touch that path; it is a separate follow-up.

An OS-level race, also found in stress testing: an open that arrives within moments of the app process exiting can be refused by LaunchServices with error -600 (procNotFound), so the app does not start at all. There is no crash and no report. With `open -a` the error prints in the terminal; what a Finder double-click shows in that instant (nothing, or a Finder alert) was not observed. Opening again a second or two later works (10/10 with a 2 s gap). The race is in LaunchServices while the app quits, not in this change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `02537eb17ded`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
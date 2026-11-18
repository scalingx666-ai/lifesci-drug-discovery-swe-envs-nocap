# Issue

**Title:** Native prompts: Esc and closing the box always cancel on Windows

## Description

## Summary

On Windows, pressing Esc or closing a destructive confirmation box ran the destructive action.

A confirmation whose only action is destructive (the two-button "Delete the kept drawing?" box) put the action in the dialog's cancel slot, so that Return would be safe. On Windows, rfd 0.16.0 shows a TaskDialog where Esc and the close box return `IDCANCEL`, and tauri-plugin-dialog 2.7.1 (`desktop.rs`) remaps that to the cancel slot's label, so Esc returned "Delete".

Owner decision ("Esc safe now"): on Windows, Esc and close always cancel, and Return picks the action.

- **Windows and Linux:** `{ ok: <action>, cancel: "Cancel" }`. Esc and close cancel; Return runs the action.
- **macOS:** unchanged (`{ ok: "Cancel", cancel: <action> }`). AppKit gives Esc only to the button titled "Cancel".
- The platform is a parameter that defaults to detection, so one test host covers every branch.
- Fails closed: only an exact action-label result runs an action. Anything else cancels.
- Removes #195's known-issue comment and turns on its skipped test (`pageGrowthPrompt.test.ts`).

## Callers

Only the two-button Delete confirmation changes layout. These prompts already had Cancel in the cancel slot, so Esc and close already cancelled on both platforms, and they are now covered by tests:

- the three-button kept-drawings prompt (Save Drawing… / Delete / Cancel)
- both Don't Save prompts
- Clear Overrides
- Remove Engine

The assistant's Enlarge Page box isn't destructive and is unchanged.

## Tests

- `nativePrompt.test.ts` models rfd's and the plugin's per-platform result mapping for 1-, 2- and 3-button boxes. For every destructive prompt it asserts that Esc and close cancel, what Return does, the exact macOS layouts, and that unexpected result strings cancel.
- Full `pnpm vitest run`: 8951 passed, 0 failed.
- `pnpm lint`, `pnpm build` and `git diff --check` pass.
- No Rust changes.

## Platforms

- **macOS:** layouts unchanged; verified by tests only.
- **Windows:** **unverified by hand so far.** It still needs the Windows run: in a dev build, press Esc, close the box, and press Return on each destructive prompt.

Build stamp `10.25.08.45-codex`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c6e3699f4e5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
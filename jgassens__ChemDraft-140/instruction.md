# Issue

**Title:** Floating toolbars keep their stacking order after a native box or file dialog

## Description

After a native message box or file dialog closed, the floating toolbars came back with their stacking order lost. On Windows, Rings ended up under Art where the two overlap. The cause: #131's suspension hides the toolbars and plugin panels while the box is open, then shows them again in label order, and each show raised the window.

**Now**
- **Order recorded:** when the first suspension begins, the real window order is read on the main thread: `EnumWindows` top-down on Windows, `+[NSWindow windowNumbersWithOptions:]` on macOS. `UtilitySuspension` keeps a bottom-to-top restore order for the whole cycle.
- **Restored relative to its own windows, never globally:** Windows uses `SetWindowPos` relative to sibling or owner HWNDs, with no activation and no owner reordering. macOS uses `orderWindow:relativeTo:`. A ChemDraft toolbar can't land above another app's window or dialog, and restoration waits while the app is inactive.
- **Multi-pass restores keep the order:** a window restored later (one that was still minimized, say) is placed relative to the siblings already back.
- **Parenting kept:** on macOS, each window's original document-child relationship is recorded, and only original children are reattached, so toolbars stay unparented and don't move with the document. A plugin panel created *during* a box gets the parenting normal creation gives it.
- **Unchanged:** if the order can't be read, the old order is used and the log says why. Only windows that were visible and not minimized come back, quitting behaves as before, and nested boxes keep the first snapshot.

**Tests:** 18 suspension tests on the pure logic, covering order, minimized retries, three windows over two passes, windows closed during a suspension, nested acquire, original vs new parenting. `cargo fmt` ✓, `clippy -D warnings` ✓, `cargo test`: 268 ✓ (macOS); `pnpm lint` ✓. Both `cfg` sides compile in CI.
**Platforms:** native window code on both. A Windows hands-on run (Rings over Art, box or file dialog, order and focus kept) and a macOS hands-on run are pending. The Windows session is offline for a break, and the Mac screen is locked.

History: Sol started it (stopped at model capacity), Opus finished it, Sol fixed four rounds of Astra's findings: global `HWND_TOP`; multi-pass order; macOS reparenting; deferred panels.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4ca3ba56bd4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
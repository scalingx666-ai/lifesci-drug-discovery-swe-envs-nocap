# Issue

**Title:** Let the keyboard reach canvas context-menu items

## Description

## Summary
The canvas page and object context menus never took keyboard focus, so Arrange and Copy As could not be reached without the mouse, and after an item ran focus fell to the page body (confirmed on Windows with a real keyboard).

- Opening a canvas context menu focuses its first enabled item.
- Up/Down, Home/End, Right/Left for the Arrange and Copy As submenus, Return/Space and Escape work as in the other menus.
- Shift+F10 and the Menu key open the object menu for the current selection, or the page menu when nothing is selected. The handler only runs when the canvas itself has focus, so text fields, the in-canvas text editor and plugin prompts are unaffected. Shift+F10 is not bound anywhere else (shortcut registry, toolset registry, native menus).
- Every way the menu closes, including its object being deleted, returns focus to the canvas, so Undo and tool shortcuts keep working; focus is never pulled back from a dialog or native window an item opened.
- Mouse behaviour is unchanged.

## Windows: WebView2 context menus switched off natively
On Windows, dismissing WebView2's own context menu (the browser menu, or the text-field editing menu) left the window ignoring all real mouse and keyboard input until restart. **This freeze is present on main today** (Shift+F10 with nothing focused opens the browser menu, then input wedges); this PR's text-field change would have opened a second path to it. Every ChemDraft webview window (document, dialogs, palettes, popovers, tooltips, plugin panels, Preferences, 3D debugger) now calls one helper that sets `ICoreWebView2Settings::SetAreDefaultContextMenusEnabled(false)`; failures are logged and never block a window. The page-level suppression stays as a second layer. Windows text fields keep Ctrl+X/C/V/A but lose the right-click Cut/Copy/Paste menu (an app-drawn one is a follow-up); macOS is unchanged. Native `<select>` popups do not freeze. Tested only in a Windows VM (VMware); whether the freeze also occurs on physical hardware is unknown.

## Tests
- `canvasContextMenu.dom.test.tsx` mounts the real MainWindow and sends real keyboard events: keyboard opening with and without a selection, navigation to Arrange > Row and Copy As, Return and Space, Escape, deletion while open; asserts `document.activeElement` is the canvas each time.
- Lint OK; MainWindow suites 389 passed / 1 skipped. The full suite runs in CI (not run locally while another worker was active).
- `docs/manual-stress-checklist.md`: keyboard use of the canvas context menu on both platforms.

## Platforms
- Windows: real-keyboard hands-on passed for keyboard opening, BODY focus, text editor, dialogs; the native WebView2 switch needs a cold-launch check (WebView2 may apply some settings only at the next navigation).
- macOS: hands-on queued.

Reviewed by Kimi K3 (changes requested, all fixed) and Claude Opus (no findings).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3af90208d590`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
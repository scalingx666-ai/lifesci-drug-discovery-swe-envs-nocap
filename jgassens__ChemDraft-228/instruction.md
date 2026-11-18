# Issue

**Title:** Let the click that ends text editing only commit the text

## Description

## Summary
While editing an in-canvas text object, the canvas press that ended editing went on into the active tool's handlers. With Bond restored after text placement (`restoreToolAfterTextPlacement`), that **same click** dropped a bond; with Select it changed the selection; and keyboard focus was left on the page body. Seen on macOS and Windows.

- The press that ends editing is consumed at capture: it commits through the existing path and focuses the canvas region. No bond, no selection change.
- **Only that one press** is consumed. The next click acts normally; with Bond restored by design it draws.
- Presses inside the editor, and on the edited text's own resize handles, keep the edit open as before.
- Escape, Tab, toolbar actions, double-click editing and IME composition are unchanged (a canvas press during a composition does not commit). Return adds a new line inside the text, as on main.

## Tests
`MainWindow.textCommit.dom.test.tsx` (real MainWindow, macOS and Windows variants), written to fail on main first:
- commit click with Bond / Select on empty canvas and on an atom → text committed, document and selection unchanged, focus on the canvas region;
- next click, exact: Bond on empty canvas adds one standalone bond (+1 bond, +2 atoms); Bond on an atom adds one bond and one atom in the same molecule; Select on empty canvas clears the selection; Select on an atom selects that atom (a part selection inside its molecule, per the selection policy);
- presses inside the textarea stay available for text selection; resize handles of the edited text start a resize and editing continues; Enter/Escape do not swallow the next press; composition protects the edit.

Lint OK; MainWindow, canvasContextMenu and plugins suites 1575 passed; full vitest 9981 passed (1 failure in the known `tools/agent-skill/stress/runner` flake, logged separately). No Rust changes.

## Platforms
- macOS and Windows: hands-on pending (checklist line added).

Reviewed by Kimi K3 (changes requested, fixed; re-review no findings).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `373f5111d302`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Text tool: a click on a shape, arrow or image starts a new text there

## Description

With the Text tool, a click on a shape, an image, a reaction arrow, a bracket or any other object that is not a text or a molecule did nothing. It now starts a new text at the click point, the same as a click on empty page. Labelling a reaction arrow by clicking on it now works.

**Cause.** The object's hit target took the press first. The object handler's Text-tool branch only knew texts (reopen) and atoms, so it stopped the press, and the page's new-text path never ran.

**Fix** (`apps/desktop/src/MainWindow.tsx`, object pointer handler). A Text-tool press on any object other than a text or a molecule now takes the page's `applyTextDocumentAtPoint` path:
- one new text at the press point, with its editor open;
- one undo entry.

What stays the same:
- Texts still reopen for editing, and atoms keep their behaviour; both branches run first.
- Handles on a selected object keep their own handlers.
- Every other tool behaves as before.

Label-like objects (superatom, R-group and generic atom labels, annotations, electron marks) swallowed the press on main, so no existing behaviour is lost. A new, independent text on top keeps the chemical label intact.

**Tests** (`apps/desktop/src/textOnShape.dom.test.ts`)
- One test per object type: one text at the point, editor focused, one undo entry.
- Unchanged: Shift-click, handle presses, text reopen, the atom path, and the Select tool on a shape.
- The shape case fails on main.

**Reviews:** Astra APPROVE, then APPROVE again on the extension to all object types.

**Platforms:** macOS: tests; packaged check in the morning. Windows: hands-on run requested.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a1e0c175b2a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
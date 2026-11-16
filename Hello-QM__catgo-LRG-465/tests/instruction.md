# Issue

**Title:** fix(docs): Render toggle joins the Monaco header (was floating over Save)

## Description

## Symptom

#462 fixed the **Edit** button (markdown preview header), but switching to edit view still showed the **Render (渲染)** toggle as a floating overlay — sitting on top of MonacoEditorPanel's Save status in the top-right corner.

## Fix

Same pattern as #462: `MonacoEditorPanel` gains an `edit_action` prop rendered in its own header controls (before Visualize/Save, same `.editor-btn` styling). DocViewer passes the Render toggle through it for markdown/html **edit** views. The absolute overlay remains only for `HtmlView` — the one renderer with no header row.

## Tests

Viewer suites: 42 pass.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `520b6251f268`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
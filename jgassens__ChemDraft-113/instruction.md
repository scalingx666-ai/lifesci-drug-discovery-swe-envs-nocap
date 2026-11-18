# Issue

**Title:** Plugin proposals: name a closed document correctly

## Description

## Summary

Two follow-ups from the document-tabs work (#102):

- A pending plugin proposal whose document was closed now always shows **"<title> (closed)"** in the Plugin Proposals window, also when the only open tab was closed with its ×. (Before, a single-tab guard left it unlabelled until Accept failed.)
- The label and the "its document was closed" message use the document's title **at the moment it closed**, after any Save As, not the title it had when the proposal was made.

A proposal for the only open tab still shows no document name.

## Files changed

- `apps/desktop/src/MainWindow.tsx`: `proposalDocumentName` and the accept-refusal message.
- `apps/desktop/src/plugins/createPluginRuntime.ts`: the proposal-to-tab map keeps the owner's current title.
- `apps/desktop/src/MainWindow.tabs.dom.test.tsx`: regression tests.

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 306 files, 6116 tests pass

## Platforms

- macOS and Windows: real-input runs to follow (needs a plugin that makes proposals)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `17fc6eb73207`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Text objects: typing the word "Text" no longer selects it as the placeholder

## Description

## Summary

A new text object starts with the placeholder "Text", selected so the first key replaces it. The editor decided what counted as the placeholder by comparing the content with the string "Text", and re-ran that check on every keystroke. So typing a text that reads "Text" (e.g. **"Text on top"**) selected everything the moment it read "Text", and the next key replaced it: "Text on top" became " on top". Found on Windows by real input; also on main.

The placeholder is now tracked explicitly: it's selected only right after insertion, until the first edit. After that, "Text" is ordinary text, also when an existing text object is edited again.

## Files changed

- `apps/desktop/src/MainWindow.tsx`: insertion-only placeholder flag; the three string comparisons removed.
- `apps/desktop/src/atomLabelEditFocus.dom.test.ts`: regression tests.

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 306 files, 6128 tests pass

## Platforms

- macOS and Windows: insert a text, type "Text on top" key by key, check every character stays

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `658d34992a08`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
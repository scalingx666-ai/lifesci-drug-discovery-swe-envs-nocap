# Issue

**Title:** Windows updater: show release notes as plain text

## Description

## Problem
In the 0.3.7 → 0.3.8 update test on Windows 11 (2026-10-04), the **ChemDraft Update** dialog showed the `latest.json` notes as raw Markdown (`**Report a Bug.**`, `- ` bullets), and `Help ▸ Report a Bug…` appeared as `Help • Report a Bug…` because the dialog font (Segoe UI) has no U+25B8.

## Change
- New `apps/desktop/src/updateNotesText.ts` — `updateNotesPlainText()` turns the notes into plain text: drops `**`/`__`/`*`/`_` emphasis and backticks (leaves `snake_case` alone), writes links as `text (url)`, strips heading `#`s, turns `- `/`* `/`+ ` list items into `• `, keeps paragraph breaks, and replaces ▸ ▹ ▶ ► with › (U+203A — in Windows-1252, so present in every Windows UI font).
- `updatePromptText` in `appUpdates.ts` runs the notes through it. Nothing else in the update flow changes.
- `latest.json` and the release notes stay Markdown (GitHub renders them). macOS Sparkle path untouched.
- Build stamp → `10.4.07.55-codex`.

## Tests
- `updateNotesText.test.ts`: each rule, plus the actual 0.3.8 Windows notes with the full expected output.
- `appUpdates.test.ts`: the prompt with a Markdown body contains no `**`.
- `pnpm vitest run apps/desktop/src/updateNotesText.test.ts apps/desktop/src/appUpdates.test.ts` — 19 passed.
- `pnpm lint` — passes.

## Not verified
Not seen on Windows yet: that › renders in the real task dialog is reasoned from the Windows-1252 character set, not observed. Check it in the next Windows update test.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c4084bfa74fb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
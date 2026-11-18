# Issue

**Title:** Sprout hotkeys say why they refused

## Description

## Summary

Ring hotkeys already explained why they refused. The other atom hotkeys (wedge and hashed bonds, methylidene, gem-dimethyl, cyclic bond, single bond, C=O) only said "Cannot add … here". Each refusal now names its reason:

- no free valence left;
- two free valences needed;
- no free direction to grow into;
- methylidene needs a neutral carbon;
- the target can't be edited;
- the bond already exists.

What the hotkeys place, and when they refuse, is unchanged. Success messages and the existing ring-closure reasons are unchanged.

## Files changed

- `apps/desktop/src/documentWorkflow.ts`: sprout planners return a refusal reason alongside the existing decision.
- `apps/desktop/src/MainWindow.tsx`: status lines include the reason.
- Tests: `sproutHotkeyRefusals.test.ts` (new), `userFeedbackStress.dom.test.ts`.

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 307 files, 6132 tests pass

## Platforms

- macOS and Windows: hover a full-valence atom (e.g. a quaternary carbon) and press a sprout hotkey; read the status line

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ad42485c5bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
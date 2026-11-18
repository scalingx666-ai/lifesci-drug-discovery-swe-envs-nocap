# Issue

**Title:** One label-context helper in document-workflow-core; accurate wording

## Description

## Summary
- The context a label is read with (bonded, typed, recorded bond side) now lives once in `document-workflow-core` (`nativeAtomLabelContext`, plus the `nativeAtomLabelContextInMolecule` wrapper). The app imports it instead of keeping its own copy, and `nativeExpandableLabelGroups` uses it instead of building the same context by hand. A core test pins it. No label reading changes.
- The ring-guard comments in `documentWorkflow.ts` said labels with no element are skipped; they now describe free-valence judging.
- The CDXML warning `cdxml.label_bond_side_turned` no longer implies the molecule was turned after the label was written (a cyano substituent placed left of its ring atom is drawn that way from the start). Same facts, new wording.

Follow-ups from the #92/#94 reviews. The right-side SCN fusion message is deliberately left for a separate decision.

## Tests
- `pnpm lint` passes; `pnpm vitest run`: 304 files, 6040 tests pass (17 skipped).
- New `packages/document-workflow-core/tests/labelContext.test.ts`; `bondedElementLabels.test.ts` updated for the new warning text.

## Platforms
No platform-specific code. macOS and Windows runs pending (gates on #77).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d657eafad561`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
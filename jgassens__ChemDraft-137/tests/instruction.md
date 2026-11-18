# Issue

**Title:** Page-fit suggestion: a minimum page size and live anchored-arrow bounds

## Description

Two fixes to the page-fit suggestion shown when a drawing doesn't fit its page (`recommendImportedPageFit`, shown as a button in the native box since #131):

1. **No sliver pages.** A long, flat drawing (a 30-carbon zigzag) used to get a suggested page under an inch tall. Each side now has a minimum of 26 mm (about 1 in), A10's short edge, the smallest built-in paper size. Above the minimum the drawing's shape still sets the page. Rounding still goes up, so nothing clips, and a drawing that already fits still gets no suggestion.
2. **Anchored mechanism arrows measured where they are.** The fit used an anchored arrow's stored rectangle, which goes stale once the atoms it points at move. It now uses `documentObjectInteractionBounds`, the same live geometry the selection box uses since #128.

The fused-ring cleanup tests in `documentWorkflow.test.ts` also get an explicit 30 s limit; they had timed out at 5–20 s on busy machines.

**Tests:** new cases for the flat chain (gets the minimum), an ordinary drawing (unchanged), and an anchored arrow whose atoms moved (fitted by live geometry). `pnpm lint` ✓; `documentWorkflow.test.ts` + `App.test.ts`: 800 tests ✓ (macOS).
**Platforms:** shared TypeScript logic. Windows hands-on check of the page-fit box to follow. A macOS hands-on check is pending: the Mac screen is locked, and the tests cover the logic.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91e649948449`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
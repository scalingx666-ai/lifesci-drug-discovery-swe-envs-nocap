# Issue

**Title:** Make the label tightness test independent of system fonts

## Description

## Why
Since GitHub's ubuntu-26.04 runner image (20261101), every PR fails `Types, tests, web build` on two cases in `labelQuality.test.ts` (4.88 vs < 3). The new image has different system fonts, so resvg's measured ink is shorter than the deterministic collision box. App behaviour is unchanged; only the test's absolute pixel tolerance assumed particular fonts.

## Change (test only)
- Checks that collision boxes use glyph bounds, not padded layout bounds.
- Adds fixed labels N and NH2 at 20 px with heights derived by hand from the character-extent constants (15.6 and 20.272 px, within 0.5 px), so padding added inside the shared bounds helper fails. Verified: 1 px of added padding fails both cases.
- Ink-containment checks are unchanged.

## Tests
`labelQuality.test.ts`: 20/20 on macOS. CI on Linux is the real check.

## Review
Kimi reviewed two earlier versions (too loose; then tautological) and drove this design. Final Kimi review in progress.

Unblocks CI for every open PR, including the 1.1.1 batch.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c27d4819df0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
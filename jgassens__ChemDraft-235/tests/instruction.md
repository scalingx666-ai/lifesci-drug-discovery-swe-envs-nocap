# Issue

**Title:** Move the formula formatter to document-workflow-core

## Description

## Summary

Moves the chemical-formula span formatter out of the desktop app into `@chemdraft/document-workflow-core`, so tables, reaction conditions and (later) isotope labels share one copy instead of each writing its own.

- `formulaSpansFromText` (digit runs after an element or bracket become subscripts; a trailing charge becomes a superscript) moves unchanged. The app's Format as Formula command imports it from the package.
- New `formulaSpansForMixedText(text, sourceSpans)` formats only the tokens of a line that read as a formula, and returns `undefined` when nothing changes. A token qualifies when a letter or `)`/`]` is followed by a digit and the whole token parses as element symbols (plus D and T), common group abbreviations, brackets, counts, an optional leading coefficient, `·` hydrates (decimal coefficients allowed) and an optional trailing charge. Trailing `, ; : . ! ? * † ‡` are ignored. The scan is linear in token length (timing test included).
  - `CH2Cl2, −20 °C, 4 h` → CH₂Cl₂, −20 °C, 4 h
  - `1. Ti(OiPr)4 (5 mol%)` → Ti(OiPr)₄
  - `NaBH4.` → NaBH₄.
  - `D2O`, `CDCl3`, `CaSO4·0.5H2O` are formatted
  - `3 equiv`, `5 mol%`, `−78 °C`, `(+)-DET`, `1.00` are unchanged
  - `13CH3I` keeps `13` plain; a `TODO(isotopes)` marks it for the isotope work.
- **What changes for existing callers: nothing.** The only existing caller is the app's Format as Formula command, through `formulaSpansFromText`. That code is moved byte-for-byte, and its unit tests moved unchanged and pass in the package. The D/T symbols, the trailing-punctuation rule, the decimal hydrate coefficients and the token guard belong only to the new `formulaSpansForMixedText`, which nothing in the app calls yet. Its own tests cover each of them.
- The package boundary test now skips `*.test.ts` files in its declared-dependency check: that rule is about run-time imports, and the moved tests import `vitest`, which runs from the repository root. The forbidden-import checks still scan every file.
- Build stamp bumped.

## Not in this PR

- `[Cu(NH3)4]2+` still formats the `2` as a subscript and only `+` as the charge. That is the moved function's existing charge rule (one digit is a charge only after a single element symbol). Fixing it changes Format as Formula too, so it gets its own follow-up PR.

## Tests

- `pnpm lint` clean.
- `vitest`: document-workflow-core and `apps/desktop/src/documentWorkflow.test.ts`, 1173 tests pass.
- `git diff --check` clean.
- CI runs the full suite on Linux, macOS and Windows.

## Platforms

Pure TypeScript with no platform branches. CI covers Windows; nothing was run by hand on either platform because nothing here is interactive.

## Review

- Kimi reviewed the move (behaviour-preserving, no stale references, boundary change scoped) and found four issues in the new helper. All four are fixed in the second commit, and Kimi's re-review of that fix found nothing.
- Opus reviewed the stamp bump.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fbf0c00ddba7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
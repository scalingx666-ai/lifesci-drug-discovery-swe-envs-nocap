# Issue

**Title:** CDXML: import every element by atomic number, never as carbon

## Description

## Summary

**CDXML import turned most elements into carbon, silently (AGENTS.md §7).** `cdx-compat`'s `elementToAtomicNumber` knew only H–Ca, Br and I, and `elementFromCdxmlAtom` fell back to `"C"` for any other numeric `Element`. So iron (26), zinc (30), copper (29), nickel (28), palladium (46), platinum (78), tin (50), selenium (34), mercury (80), gold (79), and every element past calcium except Br and I, opened as carbon with no warning. On export, those elements were written as text with a warning instead of their atomic number.

- **One element table, in the native model.**
  - `packages/chem-core/src/elements.ts` now exports `elementSymbols`, an ordered list of all 118 symbols where index Z−1 is element Z, plus `elementSymbolForAtomicNumber` and `atomicNumberForElementSymbol`.
  - `molfile.ts` builds its symbol set from it (plus D, T, `*`) instead of keeping its own copy.
  - `cdx-compat`, which already depends on chem-core, maps numbers through it, and its partial table is deleted. No new cross-package dependency (§6).
  - layout-engine's and rdkit-adapter's own lists are untouched; deduplicating those is separate.
- **An Element that names no element warns instead of becoming carbon.** That covers 0, 119, a fraction, a negative number, `"Xx"`, and an empty value.
  - The atom imports as an unknown atom `*` and keeps its bonds.
  - A `cdxml.atom_element_unknown` warning names the CDXML node and the raw value, for example: `CDXML atom a1 has Element="119", which names no element; imported as an unknown atom (*).`
  - The rest of the file still opens (§13).
  - A **missing** attribute stays carbon, the CDXML default.
  - A literal symbol, either a real element or D or T (which this exporter wrote as text), is accepted as written.
- **Export** writes `Element="<atomic number>"` for every element. Non-element labels (D, T, `*`, abbreviations) keep today's text-plus-warning; rewriting D/T as H with an isotope is out of scope.

Our own CDXML files reopen from their embedded native payload. These changes affect the visible atom layer: files from other programs, and payload-less files.

## Tests

`packages/cdx-compat/src/index.test.ts`, new `describe("CDXML element numbers")`:
- Fe, Zn, Cu, Ni, Pd, Pt, Sn, Se, Hg and Au import by atomic number with no warning.
- Every number from 1 to 118 imports to its symbol.
- A missing `Element` stays carbon, with no warning.
- The literal symbols `Fe`, `D`, `T` and `Og` are accepted.
- `0`, `119`, `Xx`, `26.5`, `-6` and `""` each import as `*` with both bonds kept and exactly one warning naming node `a1`, the raw value, and the molecule.
- Round trip: import → `exportDocumentToCdxml` writes `Element="26"` etc. with no `atom_element_symbol_exported` warning → the visible layer alone re-imports the same elements.
- The existing dative-bond fixture now asserts its acceptor is **copper**. `Element="29"` was being read as carbon, and nothing checked.

**Fixtures** (`b973e7f`), registered in `packages/fixtures`:
- `packages/fixtures/cdxml/ten-metals.cdxml`: C–M–Cl fragments for the ten metals above, each written by atomic number. On `main` all ten opened as `C-C-Cl`.
- `packages/fixtures/cdxml/invalid-element.cdxml`: O–X–N with `Element="119"`. It opens as `O-*-N`, with the warning naming node `a2`.

cdx-compat tests open both by name, and they double as the owner's hands-on files.

`packages/chem-core/src/elements.test.ts` (new): 118 distinct symbols in order, number↔symbol in both directions, and nothing returned outside 1–118, for fractions, or for D, T, `*` or labels.

No shared fixture changes meaning: across fixtures and tests, the only Element number outside the old table was those two copper atoms.

## Platforms

- **Windows:** `pnpm lint` ✅; full `pnpm vitest run` on `c36b8c6` in the heavy slot ✅ 4622 passed, 0 failed; `git diff --check` ✅. CI on `c36b8c6`: all 4 checks ✅ (clippy `-D warnings` and `cargo test` on macOS and Windows; no Rust changed). Headless check of the owner files: `ten-metals.cdxml` opens as C–Fe–Cl … C–Au–Cl (main: C–C–Cl ×10); `invalid-element.cdxml` opens as O–*–N with the warning (main: O–C–N, silent).
- **Catch-up after #86 (`cc85c8d`):** a merge of `origin/main` (#77, #82, #86), with no rewrite. The only conflict was the stamp, now a fresh `10.10.17.49-opus`; the diff against `main` is exactly this PR's files. #77's centred double-bond change in `cdx-compat/src/index.ts` merged cleanly. Results: `pnpm lint` ✅; focused vitest on cdx-compat, fixtures and chem-core ✅ (13 files, 326 passed); `git diff --check` ✅.
- **macOS:** not verified; platform-neutral TypeScript, no native code.

## Gates

- [x] Stress test: the §14 gauntlet on `c36b8c6` (lint, full vitest, diff --check; Rust gates in CI)
- [x] Owner hands-on check: **pass** (2026-10-10 17:43 CDT), on the packaged branch build at `8e50252`. The ten metals import by atomic number, and `Element="119"` keeps its bonds as `*`, with 3 warnings.
- [x] Review: claude-fable `fable-pr88-20261010` APPROVE WITH NITS (fixed in `e283cd8`); re-review `fable-pr88-rr-20261010` APPROVE (one nit declined: a Unicode minus reads as a label, which is visible, not silent).

## Note for #83

The OMe session's #83 adds Pr 59, Ac 89 and Ts 117 to the old partial table. This PR deletes that table, so whichever lands second resolves the conflict by dropping #83's three entries; the full table covers them.

## Squash-merge message

```
CDXML: import every element by atomic number, never as carbon

The CDXML importer knew the atomic numbers of H–Ca, Br and I only, and
read every other Element number as carbon without a word (iron, zinc,
copper, palladium, platinum, gold…). chem-core now owns one ordered
118-element table that molfile and cdx-compat both use. A number that
names no element (0, 119, a fraction, a sign, an exponent or hex form)
or an empty value imports as an unknown atom "*" that keeps its bonds,
with a warning naming the CDXML node and the value. A missing attribute
stays carbon; non-numeric text (symbols, D, T, *, labels such as Ph
and OMe) is taken as written, as before. Export writes atomic numbers
for every element.

```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67ac8e9b5c35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
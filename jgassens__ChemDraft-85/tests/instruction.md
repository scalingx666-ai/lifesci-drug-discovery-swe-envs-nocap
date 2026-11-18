# Issue

**Title:** Typed NH no longer becomes nihonium: fold label case only when unambiguous

## Description

## Summary

Typing "NH" on a ring nitrogen turned it into **nihonium**. `normalizeNativeAtomElementLabel` (layout-engine) folded any label's case blindly, so a label that case-folds to an element symbol became that element:
- "NH" → Nh (nihonium)
- "CO" → Co (cobalt)
- "CN" → Cn (copernicium)
- "NO" → No (nobelium)
- "HS" → Hs (hassium)
- "PO" → Po (polonium)
- "HO" → Ho (holmium)

They were never badged (outside the covalent tables), and they were counted and exported as those elements.

The rule now (owner-approved via the coordinator, 2026-10-10; list per review ruling):
- **An exact symbol is its element:** "Co" is cobalt, "Nh" is nihonium, "Si" is silicon.
- **Any other case folds to the element** ("cl"/"CL" → Cl, "si"/"SI" → Si), **except eleven two-letter group labels**, which stay as typed and read as the two atoms they spell. The list is explicit in code and is chemical judgement, not a derived rule.

Of the 118 symbols, only the 26 two-letter ones whose capitals split into two one-letter symbols are affected:

| Typed (capitals or lower case) | Reads as | Why |
|---|---|---|
| `NH` | N + H | a ring N–H (pyrrole, indole), not nihonium |
| `CO` | C + O | carbonyl, not cobalt |
| `CN` | C + N | cyano, not copernicium |
| `NO` | N + O | nitroso, not nobelium |
| `HO` | H + O | hydroxyl written right to left, not holmium |
| `HS` | H + S | thiol written right to left, not hassium |
| `PO` | P + O | phosphoryl, not polonium |
| `CS` | C + S | thiocarbonyl, not caesium |
| `HF` | H + F | hydrogen fluoride, not hafnium |
| `BH` | B + H | a borane ring vertex, not bohrium |
| `CF` | C + F | a fluorinated carbon vertex, not californium |
| `SI` | Si | S + I is not a group anyone writes |
| `CU` | Cu | C + U is absurd |
| `NI` | Ni | N + I is not a group anyone writes |
| `PB` | Pb | P + B is not a group anyone writes |
| `SN` | Sn | S–N is not a common group label (the one judgement call; the first brief listed it as a formula) |
| `SC` | Sc | thiocyanate is written SCN; "SC" alone is no group |
| `OS` | Os | O–S alone is no group label |
| `IN` | In | I + N is no group label |
| `BI` | Bi | B + I is no group label |
| `NB` | Nb | N + B is no group label |
| `NP` | Np | N + P is no group label |
| `SB` | Sb | S + B is no group label |
| `YB` | Yb | Y + B is no group label |
| `BK` | Bk | B + K is no group label |
| `PU` | Pu | P + U is no group label |

For the eleven, lower case ("nh", "co") also stays as typed. On its own that text counts nothing; with #83 it is badged as unrecognized. It is never silently nihonium or cobalt.

Every relabel path calls this one function: the inline label editor, the hover hotkeys (`applyNativeAtomElementTarget`), and text converted to an atom (`convertNativeTextObjectToAtom`, which now leaves "NH"/"CO" as text instead of making a nihonium or cobalt atom).

**Old files** store exact symbols (labels were folded on entry), so they reopen unchanged. A file that saved a mistaken "Nh" keeps it; nothing changes silently. Tested.

## For the owner: hands-on check (gate 2)
1. Draw indole (or paste `c1ccc2[nH]ccc2c1`). Hover the ring nitrogen and type `NH`, then press Enter. The label reads NH and the formula reads **C8H7N**, with no "Nh" anywhere.

## Interaction with #82
#82's `labelReading.test.ts` pins today's behaviour ("NH" → Nh, "CN" → Cn). Whichever of the two PRs merges second flips those expectations and, once "CN" is free, adds cyano (`*C#N`, 1 bond) to the abbreviation table.

## Files changed
- `packages/layout-engine/src/valence.ts`: `normalizeNativeAtomElementLabel` and the explicit `nativeFormulaTwoLetterLabels` list.
- `packages/layout-engine/src/elementLabel.test.ts`:
  - every element symbol exact;
  - the 26 splitting symbols pinned one by one in capitals and lower case;
  - a check that the 26 are exactly the splitting ones;
  - every other two-letter symbol still folding.
- `packages/document-workflow-core/tests/elementCaseFolding.test.ts`: NH on pyrrole and indole (Kekulé and aromatic bonds) keeps C4H5N / C8H7N; CO, CN and HS on a chain end.
- `apps/desktop/src/elementCaseFolding.test.ts`: label-editor and hotkey relabels, NH back to N restoring the chemistry, text→atom, and save→reopen of an old file storing "Nh"/"Co".
- `apps/desktop/src/MainWindow.tsx`: build stamp `10.10.12.10-opus`.

## Tests run (Windows)
- Full `pnpm vitest run` on c6f0ba7 (heavy slot): 4659 tests pass and 1 fails. The failure is `joback.real.test.ts` timing out at 5.8 s/5 s under machine load. It passes 21/21 alone, and this change doesn't touch rdkit-adapter.
- On 7e692ef: the three new test files pass, 174 tests. The rest of layout-engine passes too (337 in all, including those 161).
- `pnpm lint` passes; `git diff --check` is clean.

## Platforms
Pure TypeScript with no platform branches.
- **Windows:** the tests above.
- **macOS:** verified. The owner did the hands-on check on a packaged branch build at 7e692ef (NH on indole's N reads C8H7N; an exact-case symbol keeps its element).

## Known limitations
- A document that already stores a mistaken "Nh" keeps it. The fix does not guess which old atoms were meant as N–H.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65e882a7d742`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Abbreviation table and atom-label reading (no behaviour change)

## Description

## Summary

This adds the abbreviation table and the atom-label reading, with no change in behaviour. It is the first of two PRs that make atom labels such as "OMe" mean their group. Nothing in the app calls these functions yet. #83 wires them into the badge, the formula and the exports, and #77 builds its ring-atom label rule on them.

- `packages/template-library`: an original, case-sensitive table of 31 abbreviations (below) and the deliberate placeholder labels.
- `packages/document-workflow-core`:
  - `nativeAtomLabelReading(label, { bonded? })` says how a label reads.
  - `nativeAtomLabelFreeValence(label, charge?, { bonded? })` gives the bonds a label takes.
  - `nativeLabelGroupVerdict` / `nativeLabelGroupFreeValence` judge a group's bonds.

## For the owner: the table to approve (gate 2)

Matching is case-sensitive: `OMe` is methoxy; `Ome`, `OME` and `ome` are not groups. Each group's SMILES is its definition; `*` marks the atom it attaches to. "Also, on a bond only" spellings are element symbols that name the group only on an atom with bonds (see rule 1).

| Label | Also written | Also, on a bond only | Group | SMILES (`*` = attachment) | Formula | Bonds it takes |
|---|---|---|---|---|---|---|
| `Me` | — | — | methyl | `*C` | CH3 | 1 |
| `Et` | — | — | ethyl | `*CC` | C2H5 | 1 |
| `nPr` | — | `Pr` | n-propyl | `*CCC` | C3H7 | 1 |
| `iPr` | — | — | isopropyl | `*C(C)C` | C3H7 | 1 |
| `nBu` | `Bu` | — | n-butyl | `*CCCC` | C4H9 | 1 |
| `tBu` | — | — | tert-butyl | `*C(C)(C)C` | C4H9 | 1 |
| `Ph` | — | — | phenyl | `*C1=CC=CC=C1` | C6H5 | 1 |
| `Bn` | — | — | benzyl | `*CC1=CC=CC=C1` | C7H7 | 1 |
| `Bz` | — | — | benzoyl | `*C(=O)C1=CC=CC=C1` | C7H5O | 1 |
| `COMe` | `MeCO` | `Ac` | acetyl | `*C(C)=O` | C2H3O | 1 |
| `OMe` | `MeO` | — | methoxy | `*OC` | CH3O | 1 |
| `OEt` | `EtO` | — | ethoxy | `*OCC` | C2H5O | 1 |
| `OAc` | `AcO` | — | acetoxy | `*OC(C)=O` | C2H3O2 | 1 |
| `OPh` | `PhO` | — | phenoxy | `*OC1=CC=CC=C1` | C6H5O | 1 |
| `CO2H` | `COOH`, `HO2C`, `HOOC` | — | carboxy | `*C(=O)O` | CHO2 | 1 |
| `CO2Me` | `COOMe`, `MeO2C`, `MeOOC` | — | methoxycarbonyl | `*C(=O)OC` | C2H3O2 | 1 |
| `CO2Et` | `COOEt`, `EtO2C`, `EtOOC` | — | ethoxycarbonyl | `*C(=O)OCC` | C3H5O2 | 1 |
| `CHO` | `OHC` | — | formyl | `*C=O` | CHO | 1 |
| `CN` | — | — | cyano | `*C#N` | CN | 1 |
| `CF3` | `F3C` | — | trifluoromethyl | `*C(F)(F)F` | CF3 | 1 |
| `NO2` | `O2N` | — | nitro | `*[N+](=O)[O-]` | NO2 | 1 |
| `N3` | — | — | azido | `*N=[N+]=[N-]` | N3 | 1 |
| `MgBr` | `BrMg` | — | bromomagnesio | `*[Mg]Br` | BrMg | 1 |
| `Boc` | — | — | tert-butoxycarbonyl | `*C(=O)OC(C)(C)C` | C5H9O2 | 1 |
| `Cbz` | — | — | benzyloxycarbonyl | `*C(=O)OCC1=CC=CC=C1` | C8H7O2 | 1 |
| `Fmoc` | — | — | 9-fluorenylmethoxycarbonyl | `*C(=O)OCC1C2=CC=CC=C2C2=CC=CC=C12` | C15H11O2 | 1 |
| `TMS` | — | — | trimethylsilyl | `*[Si](C)(C)C` | C3H9Si | 1 |
| `TBS` | `TBDMS` | — | tert-butyldimethylsilyl | `*[Si](C)(C)C(C)(C)C` | C6H15Si | 1 |
| `Ms` | `SO2Me`, `MeSO2` | — | methanesulfonyl | `*S(=O)(=O)C` | CH3O2S | 1 |
| `Tos` | — | `Ts` | p-toluenesulfonyl (tosyl) | `*S(=O)(=O)C1=CC=C(C)C=C1` | C7H7O2S | 1 |
| `Tf` | `SO2CF3`, `CF3SO2`, `F3CSO2` | — | trifluoromethanesulfonyl | `*S(=O)(=O)C(F)(F)F` | CF3O2S | 1 |

**How a label reads**, in order:
1. **On an atom with bonds, four element symbols are groups**, because chemists write them on bonds: `Ac` → acetyl, `Pr` → n-propyl, `Ts` → tosyl, and `Ar` → aryl (a placeholder, not a structure). Unbonded, they are actinium, praseodymium, tennessine and argon. Exact case only.
2. **Element symbol**, by #85's case folding (now on main): an exact symbol is its element, and other case folds (`cl` → Cl), except eleven two-letter group labels such as `NH`, `CN` and `CO`, which stay as typed. Elements otherwise win over the table, which is why no label or alias spells one. `Cn` is copernicium; `CN` is cyano (rule 3). There is no `NC` alias, because written on a bond's right it reads as isocyano.
3. **Table abbreviation**, case-sensitive, including the right-to-left spellings.
4. **Spelled label**: one heavy element with its hydrogens, `OH` (takes 1 bond), `NH2` (1), `NH` and `HN` (2, a ring N–H), `CH2` (2).
5. **Composite**: one element carrying abbreviations, all bonded to it.
   - `NMe2` (1), `NMe` (2, the ring N-methyl), `CMe2` (2), `NHBoc`/`BocHN` (1), `OTBS` (1), `CH2Ph` (1), `SiMe3` (1), `NMe3` (0, or 1 with a + charge), `CH2CN` (cyanomethyl, 1), `SCN` (thiocyanato, 1).
   - The bonded spellings count here, since a substituent is bonded to its head: `NHAc` (acetamide N, 1), `OTs` (tosylate O, 1), `NTs` (2, the ring N-tosyl), `NPr2` (1).
   - Tin and silicon heads: `SnBu3`/`Bu3Sn` is tributylstannyl (1), `SnMe3` (1), `SiMe3` (1), `SiPr3` (1). `NBu4` takes 0 bonds as NBu4⁺ and has no valid count when neutral; `NBu3` takes 0, or 1 as NBu3⁺.
   - A lower-case letter that starts an abbreviation belongs to it, but only when the two-letter symbol couldn't head the composite itself (it has no covalent valence) and the one-letter head wouldn't be a halogen. So `NiPr2` is N + 2 iPr (not nickel), `PtBu2` is P + 2 tBu (not platinum) and `OtBu` is O + tBu, while `SnMe3` stays tin, `SiPr3` silicon, and `InBu3` is never iodine.
   - A head written directly before O (`COEt`, `SOMe`, `SO2Ph`) is **not** read: that O conventionally means C=O, which the grammar doesn't model, so the label stays unrecognized rather than becoming C–OEt.
   - `CN` is read only last, after its head (`SCN`, `CH2CN`). Written first, its N faces the head, so `CNO`, `CNS` and `CNCH2` stay bare formulas (rule 7) rather than become cyanato, thiocyanato or cyanomethyl.
   - **Cyano depends on the bond's side.** The reading context's `bondSide` is "right" when every bonded neighbour lies to the label's right, the same test that draws a hydroxyl as HO. With the bond on the right, the N faces it, meaning isocyano, an isothiocyanate or an isocyanate, so `CN`, `SCN`, `OCN` and `CH2CN` stay bare formulas, never the cyano isomer. With the bond on the left, or no side given, they read as cyano, thiocyanato, cyanato and cyanomethyl. No other label depends on its side. This is why there is no `NC` alias.
6. **Placeholder** (never a structure, never a mistake): `R`, `R'`, `R''`, `R1`–`R99`, `X`, `A`, `Q`, `M`, `Nu`, `E`, `LG`, `PG`, `?`, `*`. `Z` is left out because it is also the old name for Cbz.
7. **Bare condensed formula** with no readable connectivity (`CONH2`, `SO3H`): counted, never checked (as today).
8. **Unrecognized**: everything else, including charge or isotope text inside a label (`NMe3+`, `CD3`). `Ome` reads as unrecognized with the hint "did you mean `OMe`?".

#85 merged first, so this branch merged main and flipped the pins in 27176b6: `NH` reads as a ring N–H, and `CN` as cyano. A lone `CN` is open until a −1 charge makes it cyanide; `cn` is unrecognized with the hint `CN`.

## Files changed
- `packages/template-library/src/abbreviations.ts` (table, `bondedSpellings`), `genericLabels.ts`, `index.ts`, `abbreviations.test.ts`, `README.md`
- `packages/document-workflow-core/src/atoms.ts` (reading block only), `labelGroups.ts` (group shapes), `index.ts`, `package.json` (+ template-library), `README.md`, `tests/labelReading.test.ts`, `tests/abbreviationTable.test.ts`
- `apps/desktop/src/MainWindow.tsx` (build stamp only), `pnpm-lock.yaml`
- `packages/document-workflow-core/tests/elementCaseFolding.test.ts` (from #85; one test title now says cyano)

## Tests run (Windows)
- `pnpm vitest run packages/template-library packages/document-workflow-core` on cc22229: 5 files, 226 tests, all pass. They cover:
  - every entry against the element table, the native valence model, and RDKit's reading of its SMILES;
  - the bonded-only spellings, element unbonded and group bonded;
  - the free valence per entry and per composite;
  - composites with Ac/Pr/Ts and the lower-case rule;
  - case variants, empty and whitespace labels, charge and isotope text, and the "Ar" rule.
- After merging main and adding cyano, on 27176b6: `pnpm vitest run packages/template-library packages/document-workflow-core packages/layout-engine/src/elementLabel.test.ts apps/desktop/src/elementCaseFolding.test.ts`, 8 files, 406 tests, all pass. Cyano passes the same element-table, valence-model and RDKit checks as every entry.
- `pnpm lint` passes; `git diff --check` is clean.
- Not run locally: the full `pnpm vitest run`, `pnpm build` and the cargo steps. The machine is limited to one heavy job at a time, and the coordinator accepted CI on three hosts as the full-suite gate: there is no Rust change and no caller.

## Review
- Kimi (kimi-pr82-20261010): approve with nits, fixed in 18f5512. Re-review approved, no findings (fable-pr82-rereview-20261010).
- d077852 adds the Ac/Pr/Ts rule the coordinator asked for before the owner sees the table.
- Re-review of d077852 (fable-pr82-rr2-20261010) requested changes: the lower-case split turned SnMe3/SiPr3/InBu3 into sulfur or iodine. 2dbc317 fixes that, and cc22229 adds "Bu" as n-butyl so SnBu3/Bu3Sn read as tributylstannyl.
- Re-review of d077852..cc22229 (fable-pr82-rr3-20261010): approved with nits; the coordinator closed the review gate. The nits are the test count and the BiPr3 limitation, both in this body.
- 6bc1527 merges main (#85); 27176b6 adds cyano and flips the NH/CN pins.
- Re-review of cc22229..27176b6 (fable-pr82-rr4-20261010) requested changes: the order-agnostic composite tokenizer read `CNO`, `CNS` and `CNCH2` as the wrong isomers. 57490ea makes `CN` trailing-only and pins those three as bare formulas; the same 406 tests pass, with lint and diff-check clean. Re-review approved (fable-pr82-rr5-20261010); the owner approved the table and reading rules.
- 67d9312 and 261d003 merge main (#80, #84); only the build stamp conflicted.
- Codex (on 67d9312, P2): `OCN`/`SCN` with the bond on the right would be read as the wrong isomer. 74bbe0d adds `bondSide` and declines that reading (rule 5 above); 8 files, 407 tests pass, with lint and diff-check clean.

## Platforms
Pure TypeScript with no platform branches. Windows: the tests above. macOS: no platform code, and the coordinator waived the Mac check.

## Known limitations
- Nothing uses the reading yet; #83 wires it in.
- `BiPr3` reads as B + 3 iPr (triisopropylborane), not bismuth. The string is genuinely ambiguous, because B(iPr)3 is a real compound written that way. A bismuth tripropyl has to be written with exact-case `Bi` and a non-split group (`Bi(nPr)3` is not read; draw the atoms).
- The table is a first set. Missing groups read as unrecognized, never as a wrong structure.
- **Isocyano, isothiocyanate and isocyanate are not in the table.** A cyano-family label with its bond on the right is therefore a bare formula (counted, not checked, exported as a placeholder) rather than its real group. The side is read from the bond's direction only; a near-vertical bond counts as "left", like OH.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e51f13f056e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
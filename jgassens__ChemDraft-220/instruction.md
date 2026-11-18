# Issue

**Title:** Read molfile atom and bond counts from their fixed columns

## Description

## Summary
A V2000 molfile gives its atom and bond counts in fixed three-character columns (1–3 and 4–6). With 100 or more of each, the numbers touch (`266267`). The clipboard reader split that line on spaces, read one huge atom count, and walked off the atom block. Pasting or importing any large molecule failed with an "invalid coordinates" error: roughly 100+ atoms and 100+ bonds, which includes mid-sized molecules once explicit hydrogens are counted.

The clipboard adapter now reads the counts by column, as the CTfile spec says. A bounded fallback for short counts lines from other writers is kept, and it can never mis-split adjacent fixed-width numbers.

## Audit
Ten other molfile readers in the repo already read by column and are unchanged:
- `chemistry-adapter`
- `ocl-adapter`
- `rdkit-adapter` (`conformer`, `interpretations`, `ionization`)
- `chemdraft-cli` (`document`, `nmr`)

## Tests
- `clipboard-adapter/src/v2000Counts.test.ts`: hand-written and real RDKit counts lines at 99/99, 100/100, 266/267 and 999/999.
- `apps/desktop/src/molfileCounts.test.ts`: a large molecule's copy → paste → re-import keeps canonical SMILES, formula, charge and atom/bond counts (AGENTS §7).
- macOS: `pnpm lint` ✓, `pnpm vitest run` ✓ (9,449), `git diff --check` ✓. No Rust changes.

## Platforms
- **macOS:** automated suites verified; native paste/import not hand-checked.
- **Windows:** unverified. It needs a paste of a molfile with ≥100 atoms and ≥100 bonds that imports with identity kept.

## Found by
The Windows hands-on of #219: a 266-atom/267-bond component failed with "V2000 atom 534 has invalid coordinates", where 534 = 266 + 267 + 1.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af1710b0844b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
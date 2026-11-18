# Issue

**Title:** Copy As SMILES: messages talk about SMILES, not about a molfile step

## Description

## Summary

Edit > Copy As SMILES goes through the shared molfile writer, so some of its warnings described a V2000 or molfile detail the user never asked for (for example "V2000 has no coordination bond type … Export V3000 to preserve it"). Those messages now describe what happened in the SMILES, and a chemistry refusal shows in the status line as "Copy as SMILES failed: <reason>". Copy As Molfile keeps its wording, and the SMILES produced is unchanged.

| Before (Copy As SMILES) | After |
|---|---|
| …the label's group is not represented in the molfile. | …not represented in SMILES. |
| V2000 has no coordination bond type: N dative bond(s) written as plain single. Export V3000 to preserve it. | SMILES conversion wrote N dative (dashed) bond(s) as plain single. |
| …written as bond type {code} ({order}), dashed style not preserved. | …written to SMILES as {order}, dashed style not preserved. |
| Aromatic bonds at atoms … preserved as type 4 (aromatic). | …the structure engine interpreted them for SMILES. |
| Literal atoms … written without a valence field, so a reader may add hydrogens. | Hydrogen counts at literal atoms … could not be specified; the structure engine may add hydrogens. |

## Files changed

- `packages/chem-core/src/molfile.ts`: format-aware messages in the shared writer (molfile wording unchanged).
- `packages/document-workflow-core/src/moleculeSmiles.ts`, `apps/desktop/src/MainWindow.tsx`: pass the SMILES context; status-line refusal.
- Tests: `moleculeSmiles.test.ts`, `MainWindow.copyAsSmiles.dom.test.ts`, `structureListExport.test.ts`.

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 308 files, 6137 tests pass

## Platforms

- macOS and Windows: Copy As SMILES on a dative-bond molecule, check the status line

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e577670a419`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
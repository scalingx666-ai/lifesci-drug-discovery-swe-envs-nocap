# Issue

**Title:** Keep Clean Up Structure 2D from overlapping atoms in fused-ring molecules

## Description

## Summary

Clean Up Structure 2D sends a molecule with a fused ring system to OpenChemLib's coordinate generator. For rhodamine (TMR) and fluorescein that layout keeps the chemistry exactly right but puts a carboxyl oxygen or a ring carbon within 0.26 to 0.47 bond lengths of a ring atom and bends one six-ring, and nothing checked the result. This PR checks every generated layout before it is committed and tries better ones when it fails.

- **A layout-quality check** (`layout-engine`, pure geometry). Hard defects: overlapping atoms (closer than half a bond), crossing bonds, an atom lying on a bond it is not part of, collinear overlapping bonds, and atom labels whose boxes touch a bond or another label. Label boxes come from the renderer's own label layout, planned on the whole molecule (metals and dative bonds included); a free metal's label against its own donors' labels is exempt, because metal placement puts them there on purpose. Soft limits: bond lengths 0.9 to 1.1 of the mean and 5/6-ring angles within 10°, with one acyclic bridge bond between ring systems allowed to stretch to 1.6. Bridged ring systems (norbornane, adamantane, calixarene macrocycles) are judged on hard defects only, since their rings fold over each other in 2D.
- **RDKit alternates** (`rdkit-adapter`): an identity-preserving 2D relayout of the same molfile with CoordGen and with the default depictor, keeping atom order and explicit hydrogens and refusing any change to the isomeric SMILES, elements, charges or isotopes.
- **A rigid-fragment repair** (`layout-engine`): turns a spiro ring system about its spiro atom, swings a pendant at a bridge or a substituent at its ring atom, never changes a ring's shape and never mirrors. Labels of moved atoms and their attachment atoms are re-planned on each trial, and the search has a fixed, deterministic budget.
- **Selection** (`documentWorkflow.ts`): an OpenChemLib layout that passes is used exactly as before, so molecules that cleaned up well are unchanged and RDKit is not loaded. Otherwise the RDKit and repaired layouts are tried, each through the existing identity and stereo read-back checks, and judged on their final placed coordinates; an RDKit or repaired winner is turned (never mirrored) so its largest ring system lies horizontal with the rest below. A layout with overlapping atoms or labels, an atom on a bond, or overlapping collinear bonds is never committed; crossings alone are allowed so cages still clean up. A repair may ignore a double bond's drawn geometry only when the bond is aromatic or lies in a ring of at most seven atoms, so E/Z never changes. When nothing beats the drawing, it is kept exactly, with a specific warning in the status. Still one undo entry.

Results (lengths in bond lengths; all committed layouts have zero hard defects):

| Molecule | Layout committed | Nearest two atoms | Closest label to a bond |
|---|---|---|---|
| TMR | RDKit CoordGen, turned to the textbook orientation | 0.69 | 0.20 |
| Fluorescein lactone | RDKit CoordGen with its spiro ring system turned, then oriented | 0.63 | 0.28 |
| Open fluorescein | RDKit CoordGen | 0.69 | 0.23 |
| Acridine, cholesterol, xanthene, TMR without the benzoate | OpenChemLib, unchanged | 1.00 | 0.27 to 0.57 |
| Norbornane, cubane | OpenChemLib, unchanged | 0.83, 0.74 | no labels |
| Adamantane | RDKit CoordGen (one crossing) | 0.55 | no labels |
| Calix[4]/[6]arene, p-tert-butylcalix[5]/[6]arene (inserted templates) | Repaired, hydroxyl labels clear | | |

Roughened hand-drawn TMR and fluoresceins clean up to the same layouts. A before/after sheet of these rows was rendered with the CLI for review.

## Test expectation changes (existing tests)

None. `documentWorkflow.test.ts` gains tests and imports `vi`; no existing line of any main test changed, including the zinc tetrakis(imidazole) fixed-point test and the calixarene perspective-template test.

## Tests run

On macOS:

- At `d60fd9a4` (main at `ac907fd8` included): `pnpm vitest run` 540 files passed, 10 skipped; 11,745 tests passed, 24 skipped, 0 failed. `git diff --check`, `cargo fmt --check`, `cargo clippy --all-targets -- -D warnings`: pass. `cargo test`: 599 passed, 9 ignored. `pnpm lint` failed on four type errors in two test files only.
- At `905db95b` (the tip; it fixes those four test type errors and changes no assertion): `pnpm lint` pass, `pnpm build` pass, `apps/desktop/src/cleanupLayoutQuality.test.ts` and `apps/desktop/src/documentWorkflow.test.ts` 671 passed.
- Speed: a 500-atom labelled repair takes about 0.2 s; a 499-atom ring chain's quality check about 60 ms.
- Packaged branch build: last built at `7fe85b2b` (`app/ChemDraft (dev).app`, label `p8-cleanup [review/p8-cleanup]`, stamp `10.31.10.00-codex`). It was not rebuilt for the later commits because another worktree's dev build was running (they share one identifier and lock).

Reviews (each a separate agentctl run; no reviewer reviewed its own code; Reviewed-by lines are in each commit):

| Run | Reviewer | Scope | Outcome |
|---|---|---|---|
| run-20261031-085528-2782f9 | Astra, high | The whole first change and the merge of main | 2 P1 (exponential ring enumeration; unbounded repair) and 3 P2 (judged before placement; fallback could commit overlaps; atom-on-bond and collinear contacts passed), fixed in `7a802eb8` and `7f406c5c` |
| run-20261031-095749-5c31b6 | Astra, high | `7a802eb8` | One P2 left (fallback allowed contacts), fixed in `7f406c5c`. One P3 declined: the ring finder can miss one of several equally short rings larger than six atoms, which nothing here uses |
| run-20261031-100716-252378 | Astra, low | `7f406c5c` | No findings |
| run-20261031-104241-38df6d | Astra, high | Label clearance, orientation, bridged rings (`0a19e9e9`) | P1: label checks made the repair stall (229 s on 500 atoms). P2: label text planned without the metal (coordinated S as SH). Fixed in `e4c32c41` |
| run-20261031-110255-b331fe | Astra, high | `e4c32c41` | P2: cached label boxes not re-planned after a turn (OMe against MeO). Fixed in `dd7b5d92` |
| run-20261031-111343-a1684f | Astra, low | `dd7b5d92` | No findings |
| run-20261031-113935-d01b43 | Astra, high | The calixarene fix (`fcb893fe`) | P1: an empty stereo answer let a trans double bond become cis. Fixed in `d60fd9a4` with a topology-only exemption |
| run-20261031-115445-cd5b56 | Astra, high | `d60fd9a4` | No findings (7/8-ring boundary, fused, bridged, shared-bond, Kekulé and 1,955 randomized checks) |
| run-20261031-120525-29e878 | Astra, low | `905db95b` (test type fixes) | No findings |

## Platforms

- **macOS:** the full test run and the checks above. Not checked by hand on screen.
- **Windows:** hands-on unverified. The change is shared TypeScript with no platform branch; CI runs the tests on Windows. A hands-on check there: paste the TMR SMILES from the regression test, select it, run Clean Up Structure 2D, and confirm no atoms or labels touch; then Undo and Redo.

## Known limitations

- TMR and open fluorescein keep a bridge about 1.57 bond lengths long: with equal bonds and regular rings a carboxyl oxygen would land on the neighbouring ring carbon.
- The repair moves one fragment at a time within a fixed budget; a layout that needs more keeps the drawing with the warning.
- The ring finder reports at most one ring per bond, so among several equally short rings larger than six atoms one can be missed; nothing in this check uses those rings.

## Not in this PR

- Using the quality check for SMILES paste or other layout paths; only Clean Up uses it.

Build stamp: `10.31.10.00-codex`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac907fd8a185`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.